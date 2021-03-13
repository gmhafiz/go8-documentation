# Build

## With Task

If you have `task` installed, simply run

```text
task build
```

It does `task check` prior to build and puts both the binary and `.env` files into `./bin` folder

## Without Task

```text
go mod download
CGO_ENABLED=0 GOOS=linux
go build -v -i -o go8 cmd/go8/main.go
```

