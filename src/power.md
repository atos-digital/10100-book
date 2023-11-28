# The Power of 10.10.0

THis is a nod to Nasa's Power of 10 coding rules for writing safety critical systems (https://en.wikipedia.org/wiki/The_Power_of_10:_Rules_for_Developing_Safety-Critical_Code). We like to spirit of these rules but as-is they are not
appropriate for writing enterprise applications. They were also based on C and 10.10.0 applications are written in Golang.
So here is our 10.10.0 rules for writing robust and maintainable enterprise code:

## 1. Avoid complex functions
We like Nasa's rule 4 (Restrict functions to a single printed page) but we're worried
someone will take it literally (Elon Musk!). So lets go with limiting cyclomatic complexity
(https://en.wikipedia.org/wiki/Cyclomatic_complexity) to 10 (warning), and 15 (critical defect). Setup a linter
in vscode to show this early on.

## 2. Keep code files small
Ideally two to three page downs should reach the end of the file. Where necessary this can be extended, but
files with thousands of lines of code is an anti-pattern. Consider breaking up the files or even creating a
new package to structure the code into smaller pieces. This is driven by keeping complexity low so the
next developer working on the codebase can become productive quickly.

## 3. Business logic should be in deterministic functions
Lets unpack this... the idea of deterministic functions is borrowed from pure functional 
programming (https://en.wikipedia.org/wiki/Purely_functional_programming), 
so business logic must be separated from state and mutable logic such as retrieving data. 
This will make business logic easier to read and test.

Consider this function
```
func CustomerDiscount(id string) float64 {
	c := LoadCustomerFromId(id)

	// vip discount
	if c.name == "Kavi" {
		return 0.1
	}

	// pensioner discount
	if c.age > 60 {
		return 0.2
	}

	return 0.0
}
```
This is not deterministic and testable as LoadCustomerFromId makes CustomerDiscount stateful and unpredictable. 

This is better:

```
// load the customer in the main control loop which calls the  
// business logic function with the customer as a parameter
func CustomerDiscount(c *Customer) float64 {
	// vip discount
	if c.name == "Kavi" {
		return 0.1
	}

	// pensioner discount
	if c.age > 60 {
		return 0.2
	}

	return 0.0
}
```
so you can deterministically test this business logic with tests like this:
```
func TestVipDiscount(t *testing.T) {
	c := Customer{
		id:      "1",
		name:    "Kavi",
		age:     30,
		product: "Laptop",
	}
	d := CustomerDiscount(&c)
	if !almostEqual(d, 0.1) {
		t.Errorf("Kavi's VIP discount is not 10%%, got %.2f", d*100)
	}
}
```

## 4. Business logic should use standard lib only
You shouldn't need more than standard lib to perform your business logic. Avoid creating dependencies
that someone else will need to maintain over years to keep your business logic up-to-date. Golang
has committed to supporting standard lib indefinitely, but Jane Coder has not committed to doing this
with her library.

## 5. +80% unit test coverage
Exceptions can be made, but final production code should have 80+% unit test coverage, and 100% for
business logic. If you're using TDD then you will write the tests first, and if you're exploring an idea
you may not have any tests at the start to allow you to move quickly, but once the code is ready to
go to production it should have a high level of coverage. 

Ideally use code gutters to see coverage early.
(https://dev.to/vuong/golang-in-vscode-show-code-coverage-of-after-saving-test-8g0)

## 6. Declare variables in the smallest scope possible, no global variables
Declaring variables in the smallest scope enhances code clarity, maintainability, and reduces the risk of 
unintended side effects. When variables are confined to a limited scope, their lifespan aligns with the 
specific block of code, preventing accidental interference with other parts of the program. This 
encapsulation fosters modular design, making it easier to understand and modify code sections independently. 
Conversely, global variables introduce complexity and increase the potential for bugs, as they can be 
accessed and modified from anywhere in the program. Global variables are forbidden.

## 7. Declare functionality at the lowest most reusable level
This idea enhances code versatility and scalability. By encapsulating specific features at the lowest level, 
you can create modular components that can be easily integrated across various contexts. Consider this code
```
type Customer struct {
    ...
	product *Product
}

func (c Customer) CustomerDiscount() float64 {
    ...
	if c.product.name == "Laptop" {
		return 0.05
	}
    ...
}

type Another struct {
    ...
	product *Product
}

func (a Another) AnotherDiscount() float64 {
    ...
	if a.product.name == "Laptop" {
		return 0.07 // !!! Oops the Customer object gets 5% but AnotherObject get 7% on laptops
	}
    ...
}
```

It would be better for the Product object to declare its discount. This is better
```
type Customer struct {
    ...
	product *Product
}

type Another struct {
    ...
	product *Product
}

func (c Customer) CustomerDiscount() float64 {
    ...
	if c.product.HasDiscount() {
		return c.product.Discount()
	}
    ...
}

func (a Another) AnotherDiscount() float64 {
    ...
	if a.product.HasDiscount() {
		return a.product.Discount()
	}
    ...
}

```

## 8. Always return a value and error
Golang makes it easy to return a value an error from a function. Make sure you send a value and nil error for success 
and an error when something has gone wrong. Callers must check the err
Dont do this
```
func CustomerDiscount() float64 {
    ...
    something went wrong {
        return 0.0
    }
    return 0.1
}

...
    d := CustomerDiscount()
...
```

Do this
```
func CustomerDiscount() (float64, error) {
    ...
    something went wrong {
        return 0.0, errors.New("Customer age cannot be negative") // must be a descriptive error
    }
    return 0.1, nil
}

...
    d, err := CustomerDiscount()
    if err != nil {
        // handle error
    }
```

## 9. Do not mutate heap memory unless in a method call
Immutable heap variables offer several advantages in programming. Firstly, they simplify code by 
eliminating the need to track and manage variable state changes, reducing the likelihood of bugs 
related to mutable state. Immutability enhances code predictability and makes reasoning about program 
behavior more straightforward.

Don't do this
```
c := LoadCustomer(id)
updateAge(&c)
...
func UpdateAge(c *Customer) {
    c.Age = 1;
}
```

Restrict Age's visibility (and by convention make it lowercase "age") and use a method call like
this to update the variable
```
func (c *Customer) UpdateAge(age int) {
    c.age = age;
}
...
customer.updateAge(1)
```


## 10. Use heap memory frugally and pass around pointers instead of copying
Allocating heap memory is slow and should be avoided.

Don't do this
```
func CustomerMemCopy() Customer{
    return Customer{
		id:      "1",
		name:    "Kavi",
		age:     30,
		product: "Laptop",
	}
}
```

Do this
```
func CustomerReturnPointer() *Customer{
    return &Customer{
		id:      "1",
		name:    "Kavi",
		age:     30,
		product: "Laptop",
	}
}
```

