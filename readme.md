# Buat multi configurasi env 
java spring boot 

## Langkah2

## Langkah 1 buat 2 file application.properties
Buat 2 file dari application.properties yaitu : application-dev.properties dan application-prod.properties

## Langkah 2 lakukan configurasi 
### Untuk prod

```python
# Untuk env.prod
spring.application.name=enviroment

# port
server.port=8080

# data jpa
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# db config
spring.datasource.username=postgres
spring.datasource.password=12345
spring.datasource.url=jdbc:postgresql://localhost:5432/dummydbdev

```
### Untuk dev

```python
# Untuk env.dev
spring.application.name=enviroment

# port
server.port=8080

# data jpa
spring.jpa.properties.hibernate.dialect=org.hibernate.dialect.PostgreSQLDialect
spring.jpa.hibernate.ddl-auto=update
spring.jpa.show-sql=true

# db config
spring.datasource.username=postgres
spring.datasource.password=12345
spring.datasource.url=jdbc:postgresql://localhost:5432/dummydbprod

```