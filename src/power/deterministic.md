# Business logic should be in deterministic functions

Lets unpack this... the idea of deterministic functions is borrowed from [pure functional
programming](https://en.wikipedia.org/wiki/Purely_functional_programming),
so business logic must be separated from state and mutable logic such as retrieving data.
This will make business logic easier to read and test.

Consider this function

```go
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

```go
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

```go
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
