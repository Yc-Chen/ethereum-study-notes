
Go module is declared as in `go.mod` file.

The Go language ecosystem encourages you to define package names like `github.com/ethereum/go-ethereum/...`

Special syntax [type assertions](https://go.dev/tour/methods/15):
```go
t, ok := i.(T)
```

Go uses operators like `&` and `*` for pointer operations.

If multiple files declare `package foo`, all their functions/classes are shared under `foo.*`
