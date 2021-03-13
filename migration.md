# Migration

Migration is a good step towards having a versioned database and makes publishing to a production server a safe process.

### Create Migration

Using `Task`, creating a migration file is done by the following command. Name the file after `NAME=`

```text
task migrate-create NAME=create_a_tablename
```

Write your schema in pure sql in the 'up' version and any reversal in the 'down' version of the files

### Migrate up

After you are satisfied with your `.sql` files, run the following command to migrate your database

```text
task migrate
```

To migrate one step

```text
task migrate-step n=1
```

### Rollback

To roll back migration

```text
task migrate-rollback n=1
```

Further `golang-migrate` commands are available in its [documentation \(postgres\)](https://github.com/golang-migrate/migrate/blob/master/database/postgres/TUTORIAL.md)

