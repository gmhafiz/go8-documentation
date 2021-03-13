# Testing

## Unit Testing

Unit testing can be run with

```text
task test
```

Which runs `go test -v ./...`

In repository unit testing, it makes use of [dockertest](https://github.com/ory/dockertest) from ory that spins up temporary database in a docker to run all repositories.

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

