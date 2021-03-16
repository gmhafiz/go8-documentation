# Run

### Local

Conventionally, all apps are placed inside the `cmd` folder.

If you have `Task` installed, the server can be run with:

```text
task run
```

or without `Task`, just like in quick start section:

```text
go run cmd/go8/main.go
```

### Docker

You can build a docker image with the app with its config files. Docker needs to be installed beforehand.

```text
 task docker:build
```

Run the following command to build a container from this image. `--net=host` tells the container to use local's network so that it can access host database.

```text
docker-compose up -d postgres # If you haven't run this from quick start 
task docker:run
```

### docker-compose

If you prefer to use docker-compose instead, both server and the database can be run with:

```text
task docker-compose:start
```

