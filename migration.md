# Migration

Migration is a good step towards having a versioned database and makes publishing to a production server a safe process.

All migration files are stored in `database/migrations` folder.

## Using Task

### Create Migration

Using `Task`, creating a migration file is done by the following command. Name the file after `NAME=`

{% hint style="info" %}
By using `task`, the filename format is `{{unix_time}}_{{migration_name}}.sql`
{% endhint %}

```text
task migrate:create NAME=create_a_tablename
```

Write your schema in pure sql in the 'up' version and any reversal in the 'down' version of the files

### Migrate up

After you are satisfied with your `.sql` files, run the following command to migrate your database

```text
task migrate
```

To migrate one step

```text
task migrate:step n=1
```

### Rollback

To roll back migration

```text
task migrate:rollback n=1
```

Further `golang-migrate` commands are available in its [documentation \(postgres\)](https://github.com/golang-migrate/migrate/blob/master/database/postgres/TUTORIAL.md)

## Without Task

### Create Migration

Once `golang-migrate` tool is [installed](https://github.com/golang-migrate/migrate/tree/master/cmd/migrate), create a migration with

```text
migrate create -ext sql -dir database/migrations -format unix "{{.NAME}}"
```

### Migrate Up

You will need to create a data source name string beforehand. e.g.

`postgres://postgres_user:$password@$localhost:5432/db?sslmode=false`

{% hint style="info" %}
Save the above string into an environment variable for reuse e.g.

`export DSN=postgres://postgres_user:$password@$localhost:5432/db?sslmode=false`
{% endhint %}

Then migrate with the following command, specifying the path to migration files, data soource name and action.

```text
migrate -path database/migrations -database $DSN up
```

To migrate `2` steps,

```text
migrate -path database/migrations -database $DSN up 2
```

### Rollback

Rollback migration by sing `down` action and the number of steps

```text
migrate -path database/migrations -database $DSN down 1
```

