---
description: >-
  Go + Postgres + Chi Router + sqlx, Unit Testing Starter Kit for API
  Development
---

# Introduction

```text
        .,*/(#####(/*,.                               .,*((###(/*.
    .*(%%%%%%%%%%%%%%#/.                           .*#%%%%####%%%%#/.
  ./#%%%%#(/,,...,,***.           .......          *#%%%#*.   ,(%%%#/.
 .(#%%%#/.                    .*(#%%%%%%%##/,.     ,(%%%#*    ,(%%%#*.
.*#%%%#/.    ..........     .*#%%%%#(/((#%%%%(,     ,/#%%%#(/#%%%#(,
./#%%%(*    ,#%%%%%%%%(*   .*#%%%#*     .*#%%%#,      *(%%%%%%%#(,.
./#%%%#*    ,(((##%%%%(*   ,/%%%%/.      .(%%%#/   .*#%%%#(*/(#%%%#/,
 ,#%%%#(.        ,#%%%(*   ,/%%%%/.      .(%%%#/  ,/%%%#/.    .*#%%%(,
  *#%%%%(*.      ,#%%%(*   .*#%%%#*     ./#%%%#,  ,(%%%#*      .(%%%#*
   ,(#%%%%%##(((##%%%%(*    .*#%%%%#(((##%%%%(,   .*#%%%##(///(#%%%#/.
     .*/###%%%%%%%###(/,      .,/##%%%%%##(/,.      .*(##%%%%%%##(*,
          .........                ......                .......
```

A starter kit for Go API development. Inspired by [How I write HTTP services after eight years](https://pace.dev/blog/2018/05/09/how-I-write-http-services-after-eight-years.html).

{% hint style="info" %}
Link: [https://github.com/gmhafiz/go8](https://github.com/gmhafiz/go8)
{% endhint %}

However, I wanted to use [chi router](https://github.com/go-chi/chi) which is more common in the community, [sqlx](https://github.com/jmoiron/sqlx) for database operations and design towards more like [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html).

This kit tries to follow the [Standard Go Project Layout](https://github.com/golang-standards/project-layout) to make project structure familiar to a Go developer.

It is still in early stages, and I do not consider it is completed until all integration tests are completed.

In short, this kit is a **Go + Postgres + Chi Router + sqlx + Unit Testing Starter Kit** for API development.

## Motivation

On the topic of API development, there are two opposing camps between a framework \(like [echo](https://github.com/labstack/echo), [gin](https://github.com/gin-gonic/gin), [buffalo](http://gobuffalo.io/) and starting small and only add features you need.

However , starting small and adding features aren't that straightforward. Also, you will want to structure your project in such a way that there are clear separation of functionalities for your controller, business logic and database operations.

This is the idea behind [Clean Architecture](https://blog.cleancoder.com/uncle-bob/2012/08/13/the-clean-architecture.html). This way, it is easy to switch whichever library to another of your choice.

## Features

This kit is composed of standard Go library together with some well-known libraries to manage things like router, database query and migration support.

* [x] Router/Mux with [Chi Router](https://github.com/go-chi/chi)
* [x] Database Operations with [sqlx](https://github.com/jmoiron/sqlx)
* [x] Database migration with [golang-migrate](https://github.com/golang-migrate/migrate/)
* [x] Input [validation](https://github.com/go-playground/validator) that return multiple error strings Read all configurations using a single .env file 
* [x] \(optional\) Request log that logs each user uniquely based on host address
* [x] Cors
* [x] Unit testing of repository, use case, and handler
* [x] Scans and auto-generate [Swagger](https://github.com/swaggo/swag) docs using a declarative comments format
* [x] Custom model JSON output
* [x] Filters
* [x] Uses [Task](https://taskfile.dev) to simplify various tasks
* [x] End-to-end test using ephemeral docker containers

It has few dependencies and replacing one library to another is easy.



