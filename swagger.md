# Swagger

## Docs

Swagger UI allows you to play with the API from a browser

![swagger UI](https://github.com/gmhafiz/go8/raw/master/assets/swagger.png)

Edit `cmd/go8/go8.go` `main()` function host and BasePath

```text
// @host localhost:3080
// @BasePath /api/v1
```

Generate with

```text
task swagger
```

Access at

```text
http://localhost:3080
```

The command `swag init` scans the whole directory and looks for [swagger's declarative comments](https://github.com/swaggo/swag#declarative-comments-format) format.

Custom theme is obtained from [https://github.com/ostranme/swagger-ui-themes](https://github.com/ostranme/swagger-ui-themes)

