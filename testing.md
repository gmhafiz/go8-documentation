# Testing

## Unit Testing

Unit testing can be run with

```text
task test
```

Which runs `go test -v ./...`

In Go, unit test file is handled by appending `_test` to a file's name. For example, to test `/internal/domain.book/handler/http/handler.go`, we add unit test file by creating `/internal/domain.book/handler/http/handler_test.go`

To perform a unit test  we take advantage of go's interface. Our interfaces are defined in 

* `internal/domain/book/handler.go`
* `internal/domain/book/usecase.go`
* `internal/domain/book/repository.go`

The implementation if these interface are in separate files. For example our concrete implementation for use case of `Create` is in `internal/book/usecase/http/usecase.go`. 

### Handler

TODO

### Use Case

To perform a unit test, it needs \(depends\) a repository. However, as a unit test, we do not want to connect to a real database - we just want to isolate this use case file To solve this, one approach is to use a mocking library that can generate code for us. The library, [gomock](https://github.com/golang/mock/gomock), can be installed with 

```text
task install-gomock
```

Once installed, a mock file can be generated:

```text
mockgen -package mock -source ../../repository.go -destination=../../mock/mock_repository.go
```

Then in our `usecase_test.go` file, we create a mock database with

```go
ctrl := gomock.NewController(t)
defer ctrl.Finish()
repo := mock.NewMockRepository(ctrl)
```

Notice that now the repository is created by `mock.NewMockRepository(ctrl)`.

The `repo` variable is now available to use in our unit test in place of a real database.

### Repository

In repository unit testing, it makes use of [dockertest](https://github.com/ory/dockertest) from ory that spins up temporary database in a docker to run all repositories.

This database uses credentials defined in `.env`

```text
DOCKERTEST_DRIVER=postgres
DOCKERTEST_DIALECT=postgres
DOCKERTEST_HOST=0.0.0.0
DOCKERTEST_PORT=5434
DOCKERTEST_USER=postgres
DOCKERTEST_PASS=secret
DOCKERTEST_NAME=postgres_test
DOCKERTEST_SSL_MODE=disable
```

A container may not close properly when a unit test fails. A helper script is added to stop any container by port.

```text
task stop-dockertest
```

or

```text
scripts/stopByPort.sh 5434
```

## End to End Test

Start

```text
task dockertest
```

or

```text
cd docker-test && docker-compose down -v --build && docker-compose up -d
docker exec -t go8_container_test "/home/appuser/app/e2e"
```

Stop container

```text
task dockertest-stop
```

or

```text
docker-compose down
```

