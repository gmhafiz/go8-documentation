# Migration

## Task Runner

While the above quick start is sufficient to start the API, some tools are included for easier task management.

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

Migration is a good step towards having a versioned database and makes publishing to a production server a safe process.

## Migration

### Create Migration

Using `Task`, creating a migration file is done by the following command. Name the file after `NAME=`.

```text
task migrate-create NAME=create_a_tablename
```

Write your schema in pure sql in the 'up' version and any reversal in the 'down' version of the files.

### Migrate up

After you are satisfied with your `.sql` files, run the following command to migrate your database.

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

