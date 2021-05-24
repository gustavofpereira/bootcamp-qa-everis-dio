<h1 align="center">
:large_green_diamond: Building a Rest API for querying Brazilian cities :large_green_diamond:
</h1>

<h2 align="center">
  everis Quality Assurance Beginner by <a href=https://digitalinnovation.one/>Digital Innovation One</a>
</h2>

<p>
This repository was created as part of Bootcamp "<a href=https://www.everis.com/global/en>everis</a> Quality Assurance Beginner" by Digital Innovation One with the objective to build a REST API.

## :globe_with_meridians: Source
  
## Digital Innovation One

[Click to sign to Digital Innovation One](https://digitalinnovation.one/sign-up?ref=H395IYS4Z6)  

## :globe_with_meridians: Deploying
  
Heroku was used to publish this project, and you can see it clicking on the link below:

  - [https://instagram-class.herokuapp.com](https://instagram-class.herokuapp.com)

## :computer: Technologies

To build this project the following technologies were used:

  - [Html5](https://developer.mozilla.org/pt-BR/docs/Web/HTML/HTML5)
  - [CSS3](https://www.w3schools.com/css/)
  - [JavaScript](https://javascript.info/)

## :rocket: Installing

Just clone this repository in the folder that you want and run index.html on browser:

  `$ git clone https://github.com/gustavofpereira/instagram-class.git`
  
## :books: Sharing

Please, find bellow a guide to publish at Heroku´s platform:

  - [How to Deploy a Static Site to Heroku](https://blog.teamtreehouse.com/deploy-static-site-heroku)
  
  
# Cities API

## Requirements

* Linux
* Git
* Java 8
* Docker
* IntelliJ Community
* Heroku CLI

## DataBase

### Postgres

* [Postgres Docker Hub](https://hub.docker.com/_/postgres)

```shell script
docker run --name cities-db -d -p 5432:5432 -e POSTGRES_USER=postgres_user_city -e POSTGRES_PASSWORD=super_password -e POSTGRES_DB=cities postgres
```

### Populate

* [data](https://github.com/chinnonsantos/sql-paises-estados-cidades/tree/master/PostgreSQL)

```shell script
cd ~/workspace/sql-paises-estados-cidades/PostgreSQL

docker run -it --rm --net=host -v $PWD:/tmp postgres /bin/bash

psql -h localhost -U postgres_user_city cities -f /tmp/pais.sql
psql -h localhost -U postgres_user_city cities -f /tmp/estado.sql
psql -h localhost -U postgres_user_city cities -f /tmp/cidade.sql

psql -h localhost -U postgres_user_city cities

CREATE EXTENSION cube; 
CREATE EXTENSION earthdistance;
```

* [Postgres Earth distance](https://www.postgresql.org/docs/current/earthdistance.html)
* [earthdistance--1.0--1.1.sql](https://github.com/postgres/postgres/blob/master/contrib/earthdistance/earthdistance--1.0--1.1.sql)
* [OPERATOR <@>](https://github.com/postgres/postgres/blob/master/contrib/earthdistance/earthdistance--1.1.sql)
* [postgrescheatsheet](https://postgrescheatsheet.com/#/tables)
* [datatype-geometric](https://www.postgresql.org/docs/current/datatype-geometric.html)

### Access

```shell script
docker exec -it cities-db /bin/bash

psql -U postgres_user_city cities
```

### Query Earth Distance

Point
```roomsql
select ((select lat_lon from cidade where id = 4929) <@> (select lat_lon from cidade where id=5254)) as distance;
```

Cube
```roomsql
select earth_distance(
    ll_to_earth(-21.95840072631836,-47.98820114135742), 
    ll_to_earth(-22.01740074157715,-47.88600158691406)
) as distance;
```

## Spring Boot

* [https://start.spring.io/](https://start.spring.io/)

+ Java 8
+ Gradle Project
+ Jar
+ Spring Web
+ Spring Data JPA
+ PostgreSQL Driver

### Spring Data

* [jpa.query-methods](https://docs.spring.io/spring-data/jpa/docs/current/reference/html/#jpa.query-methods)

### Properties

* [appendix-application-properties](https://docs.spring.io/spring-boot/docs/current/reference/html/appendix-application-properties.html)
* [jdbc-database-connectio](https://www.codejava.net/java-se/jdbc/jdbc-database-connection-url-for-common-databases)

### Types

* [JsonTypes](https://github.com/vladmihalcea/hibernate-types)
* [UserType](https://docs.jboss.org/hibernate/orm/3.5/api/org/hibernate/usertype/UserType.html)

## Heroku

* [DevCenter](https://devcenter.heroku.com/articles/getting-started-with-gradle-on-heroku)

## Code Quality

### PMD

+ https://pmd.github.io/pmd-6.8.0/index.html

### Checkstyle

+ https://checkstyle.org/

+ https://checkstyle.org/google_style.html

+ http://google.github.io/styleguide/javaguide.html

```shell script
wget https://raw.githubusercontent.com/checkstyle/checkstyle/master/src/main/resources/google_checks.xml
```

<p align="right">
    <a href="https://github.com/gustavofpereira"><img alt="tagcat" src="https://github.com/gustavofpereira/gustavofpereira/blob/main/tagcat.png" width="140"></a>
</p>
