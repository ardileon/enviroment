# Buat multi configurasi env 
java spring boot 

## Langkah2

## Langkah 1 buat 2 file application.properties
Buat 2 file dari application.properties yaitu : application-dev.properties dan application-prod.properties

## Langkah 2 lakukan configurasi 
### Untuk prod

```python
# Untuk env.prod

# port
server.port=9090

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

## Langkah ke 3 lakukan configurasi applciation.properties dan pom.xml
### config.properties
Untuk membuat pilihan mengenai env yang kita select 

```python

spring.profiles.active=@activatedProperties@ 

```
### add profiles pom.xml 

```python

<profiles>
		<profile>
			<id>dev</id>
			<properties>
				<activatedProperties>dev</activatedProperties>
			</properties>
			<activation>
				<activeByDefault>true</activeByDefault>
			</activation>
		</profile>
		<profile>
			<id>prod</id>
			<properties>
				<activatedProperties>prod</activatedProperties>
			</properties>
		</profile>
	</profiles>

```

```python
### Pengertian
Pertama kita membuat 2 profile yaitu satu sebagai prod dan satunya lagi menjadi dev dengan cara memisahkannya dengan <profile></profile> 

Selanjutnya untuk mengetahuinya menggunakan <id></id>

pada <activatedProperties>...</activatedProperties> itu ditunjukan kalau kita akan mengaktifkan properties prod atau dev. 

<activation> <activeByDefault>true</activeByDefault></activation> by default maka dia kan menjalankan nya secara otomatis apabila di application.propertiesnya tidak menselect antara dev atau prod

```
### Langkah selanjutnya  
Pada terminal di vscode ketikan mvn clean install 