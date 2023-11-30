# Reusable functions

This idea enhances code versatility and scalability. By encapsulating specific features at the lowest level,
you can create modular components that can be easily integrated across various contexts. Consider this code

```go
type Product struct {
	name String
}

type Customer struct {
	product *Product
}

func (c Customer) Discount() float64 {
	if c.product.name == "Laptop" {
		return 0.05
	}
}

type Another struct {
	product *Product
}

func (a Another) Discount() float64 {
	if a.product.name == "Laptop" {
		return 0.07 // !!! Oops the Customer object gets 5% but AnotherObject get 7% on laptops
	}
}
```

It would be better for the Product object to declare its discount. This is better

```go
type Product struct {
	name String
}

func (p Product) Discount() {
	if p.name == "Laptop" {
		return 0.5
	}
	return 0.0
}

type Customer struct {
	product *Product
}

type Another struct {
	product *Product
}

func (c Customer) Discount() float64 {
	return c.product.Discount()
}

func (a Another) Discount() float64 {
	return a.product.Discount()
}
```
