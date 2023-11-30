# Always initialise with known length and capacity

Don't do this

```go
func keys(s map[string]string) {
	arr := []string{}
	for k := range s {
		arr = append(arr, k)
	}
}
```

Do this

```go
func keys(s map[string]string) {
	arr := make([]string, 0, len(s))
	for k := range s {
		arr = append(arr, k)
	}
}
```
