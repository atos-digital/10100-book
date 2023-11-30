## Do not mutate heap memory unless in a method call

Immutable heap variables offer several advantages in programming. Firstly, they simplify code by
eliminating the need to track and manage variable state changes, reducing the likelihood of bugs
related to mutable state. Immutability enhances code predictability and makes reasoning about program
behavior more straightforward.

Don't do this

```go
c := LoadCustomer(id)
updateAge(&c)
...
func UpdateAge(c *Customer) {
    c.Age = 1;
}
```

Restrict Age's visibility (and by convention make it lowercase "age") and use a method call like
this to update the variable

```go
func (c *Customer) UpdateAge(age int) {
    c.age = age;
}
...
customer.updateAge(1)
```
