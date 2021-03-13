# Tooling

## Install

The above quick start is sufficient to start the API. However, we can take advantage of a tool to make task management easier. While you may run migration with `go run cmd/extmigrate/main.go`,  it is a lot easier to remember to type `task migrate` instead. Think of it as a simplified `Makefile`.

{% hint style="info" %}
You may also choose to run sql scripts directly from `database/migrations` folder instead.
{% endhint %}

This project uses [Task](https://github.com/go-task/task) to handle various tasks such as migration, generation of swagger docs, build and run the app. It is essentially a [sh interpreter](https://github.com/mvdan/sh).

Install task runner binary bash script:

```text
sudo ./scripts/install-task.sh
```

This installs `task` to `/usr/local/bin/task` so `sudo` is needed.

`Task` tasks are defined inside `Taskfile.yml` file. A list of tasks available can be viewed with:

```text
task -l   # or
task list
```

## Tools

Various tooling can be installed automatically by running which includes

* [golang-ci ](https://golangci-lint.run/)
  * An opinionated code linter from [https://golangci-lint.run/](https://golangci-lint.run/)
* [swag](https://github.com/swaggo/swag)
  * Generates swagger documentation
* [testify framework](https://github.com/stretchr/testify)
  * Testing framework
* [gomock](https://github.com/golang/mock/mockgen)
  * Mock dependencies inside unit test
* [golang-migrate](https://github.com/golang-migrate/migrate)
  * Database Migration tool
* [sqlboiler](https://github.com/volatiletech/sqlboiler)
  * Migration tool
* [gosec](https://github.com/securego/gosec)
  * Security Checker

Install tools with

```text
task install-tools
```

## Tasks

Various tooling are included within the `Task` runner. Configurations are done inside `Taskfile.yml` file.

### Format Code

```text
task fmt
```

Runs `go fmt ./...` to lint Go code

`go fmt` is part of official Go toolchain that formats your code into an opinionated format.

### Sync Dependencies

```text
task tidy
```

Runs `go mod tidy` to sync dependencies.

### Compile Check

```text
task vet
```

Quickly catches compile error.

### Unit tests

Runs unit tests

```text
task test
```

### golangci Linter

```text
task golint
```

Runs [https://golangci-lint.run/](https://golangci-lint.run/) linter

### Security Checks

```text
task security
```

Runs opinionated security checks from [https://github.com/securego/gosec](https://github.com/securego/gosec)

### Checks

`Format Code` until `Security Checks` tasks can be run with:

```text
task check
```

### Generate Model/ORM

```text
task gen-orm
```

### Generate Swagger Documentation

```text
task swagger
```

Access at [http://localhost:3080](http://localhost:3080)

### Go generate

```text
task generate
```

Runs all `//go:generate` commands found in `.go` files.

### Test Coverage

```text
task coverage
```

Runs unit test coverage

### Build

```text
task build
```

Creates a binary of the main API, statically linked.

