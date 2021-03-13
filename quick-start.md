# Quick Start

You need to [have a go installation](https://github.com/gmhafiz/go8#appendix) \(&gt;= v1.13\) and put into path as well as [git](https://github.com/gmhafiz/go8#appendix). Optionally `docker` and `docker-compose` for easier start up.

Get it

```bash
git clone https://github.com/gmhafiz/go8
cd go8
```

Fill in your database credentials in `.env` by making a copy of `env.example` first.

```bash
cp env.example .env
```

Have a database ready either by installing them yourself or the following command. The `docker-compose.yml` will use database credentials set in `.env` file which is initialized by the previous step. Optionally, you may want redis as well.

```text
docker-compose up -d postgres
```

Once the database is up you may run the migration with

```text
go run cmd/extmigrate up
```

Finally, run the API with

```text
go run cmd/go8/main.go
```

You will see the address the API is running at as well as all registered routes.

```text
2021/01/26 18:45:22 serving at 0.0.0.0:3080
2021/01/26 18:45:22 path: /api/v1/books/ method: GET 
2021/01/26 18:45:22 path: /api/v1/books/ method: POST 
2021/01/26 18:45:22 path: /api/v1/books/{bookID} method: GET 
2021/01/26 18:45:22 path: /api/v1/books/{bookID} method: PUT 
2021/01/26 18:45:22 path: /api/v1/books/{bookID} method: DELETE 
2021/01/26 18:45:22 path: /health/liveness method: GET 
2021/01/26 18:45:22 path: /health/readiness method: GET 
```

To use, follow examples in the `examples/` folder

```text
curl --request GET --location 'http://localhost:3080/api/v1/books'
```

