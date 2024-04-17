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


### Pengertian
```bash
<profile></profile> 
```
Pada code diatas menunjukkan kita membuat 2 profile yaitu satu sebagai prod dan satunya lagi menjadi dev dengan cara memisahkannya dengan 

```bash
<id></id>
```
Selanjutnya Pada code diatas menunjukkan untuk mengetahuinya menggunakan profile apa

```bash
<activatedProperties>...</activatedProperties>
```
pada code diatas itu ditunjukkan kalau kita akan mengaktifkan properties prod atau dev. 

```bash
<activation> <activeByDefault>true</activeByDefault></activation>
```
Pada code diatas menunjukan by default maka dia kan menjalankan nya secara otomatis apabila di application.propertiesnya tidak menselect antara dev atau prod


### Langkah selanjutnya  
```bash
mvn clean install
```
Pada terminal di vscode ketikan mvn clean install . setelah code di build dalam bentuk jar (di folder target sebagai: enviroment-0.0.1-SNAPSHOT.jar)

```bash
mvn spring-boot:run
```
maka ketikan di terimnal mvn spring-boot:run untuk mengetahui dimanakah port yang berjalan dan secara default adalah 8080 yaitu dev karena di applciation.properties belum mengselect antara dev atau prod.

## Langkah ke 4 Env Prod

### Buat jar untuk env prod
```bash
mvn clean install -P prod 
```
Untuk membuat env ke arah prod karena default mengarah ke dev jadi untuk mengatasinya kita menggunakan mvn clean install -P prod dan -P prod adalah untuk supaya profilenya akan diarahkan ke prod bukan lagi ke env dev.

### Setelah itu lakukan pengetestan lagi
```bash
cd target

java -jar enviroment-0.0.1-SNAPSHOT.jar

```
Jika port yang berjalan adalah 9090 makan aplikasi sudah berjalan di env prod.

### Dan sekian terimkasih