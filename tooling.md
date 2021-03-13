# Tooling

## Task

Various tooling are included within the `Task` runner. Configurations are done inside `Taskfile.yml` file.

* `task fmt`
  * Runs `go fmt ./...` to lint Go code
  * `go fmt` is part of official Go toolchain that formats your code into an opinionated format.
* `task tidy`
  * Runs `go mod tidy` to sync dependencies.
* `task vet`
  * Quickly catches compile error.
* `task golint`
  * Runs an opinionated code linter from [https://golangci-lint.run/](https://golangci-lint.run/)
* `task security`
  * Runs opinionated security checks from [https://github.com/securego/gosec](https://github.com/securego/gosec)
* `task test`
  * Runs unit tests

All of these can be run with:

```text
task check
```

