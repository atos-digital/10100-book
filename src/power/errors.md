# Always return errors

Golang makes it easy to return a value an error from a function. Make sure you send a value and nil error for success
and an error when something has gone wrong. Callers must check the err

Don't do this

```go
func Discount(age int ) float64 {
    if age < 0 {
        return 0.0
    }
    return 0.1
}

func main() {
	// get age command line parameter
    d := Discount(age)
}
```

Do this

```go
var ErrNegativeAge = errors.New("Customer age cannot be negative")

func Discount(age int) (float64, error) {
    if age < 0 {
        return 0.0, ErrNegativeAge // must be a descriptive error
    }
    return 0.1, nil
}

func main() {
	// get age command line parameter
    d, err := Discount(age)
    if err != nil {
        // handle error
    }
}
```
