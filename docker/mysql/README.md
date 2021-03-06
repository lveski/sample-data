## MySQL

Create a derived [MySQL](https://www.mysql.com/) [docker image](https://hub.docker.com/_/mysql/) containing an initialized `test.contacts` table with all data stored in a docker volume.

See `make help` for build details.

After build and run, you can connect to MariaDB on `localhost:3306` with `test`/`test` or `root`/`root`.

## Connection info

| Name | Value  |
|--- |--- |
| user | test |
| password | test |
| database | test |
| port | 3306 |

## Run a container

```bash
docker run -d --name mysql-sample-data \
    -p 3306:3306 \
    -e MYSQL_ROOT_PASSWORD=root \
    stevetarver/mysql-sample-data:8.0.11
```

## Fetch data from command line

```bash
docker exec -it mysql-sample-data \
    mysql -uroot -proot -D test -s -e 'SELECT COUNT(*) from test.contacts;'
```

## Importing data

### MySQL Workbench: 

1. Right click on the target schema (test?) and choose `Set as Default Schema`
1. Paste into a Query window
1. Execute

OR

1. Menu Server -> Data Import
1. Select Import from Self-Contained File: select `us-500.mysql.sql`
1. Default Target Schema: test
1. Click: Start Import

Refresh the target schema

