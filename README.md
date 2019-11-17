# tsl8

A REST based implementation of [Tessellate](https://github.com/tsocial/tessellate/) (*tsl8*).

### Prerequisites

* [Go 1.13](https://golang.org/doc/go1.13)
* [Postgres DB](https://www.postgresql.org/)
* [golang-migrate/migrate](https://github.com/golang-migrate/migrate)


### Setup

#### Load database schema

[migrate](https://github.com/golang-migrate/migrate) is used for database migrations.

* Start Postgres DB service or use docker to set it up

`docker run -p 5432:5432 --env POSTGRES_USER="test_user" --env POSTGRES_PASSWORD="test_pass" --env POSTGRES_DB="tessellate" -d postgres:latest
`

* Set database URL

`export POSTGRESQL_URL=postgres://test_user:test_pass@0.0.0.0:5432/tessellate?sslmode=disable
`

* Run DB migrations

`migrate -database ${POSTGRESQL_URL} -path db/migrations up
`

> Note: To rollback use: `migrate -database ${POSTGRESQL_URL} -path db/migrations down`


