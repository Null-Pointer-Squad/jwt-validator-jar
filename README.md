# jwt-validator-jar

## How to use:
you just need to download and add this jar into your dependencies and then include it your pom.xml file 
1. first add it as a local dependency in maven using this command
   ```
   mvn install:install-file \
   -Dfile=<path-to-file> \
   -DgroupId=<group-id> \
   -DartifactId=<artifact-id> \
   -Dversion=<version> \
   -Dpackaging=<packaging> \
   -DgeneratePom=true

   ```

   Where each refers to:

<path-to-file>: the path to the file to load 

<group-id>: the group that the file should be registered under e.g → fawry.internship

<artifact-id>: the artifact name for the file e.g → jwt-validator

<version>: the version of the file e.g → 1.0-SNAPSHOT

<packaging>: the packaging of the file e.g. → jar


2. add this dependency in your pom.xml file.

```
<dependency>
			<groupId>fawry.internship</groupId>
			<artifactId>jwt-validator</artifactId>
			<version>1.0-SNAPSHOT</version>
		</dependency>
```

after that all you need to do is to use the JwrServiceImpl class like this

```

 JwtServiceImpl jwtService = new JwtServiceImpl();
String email =  jwtService.extractUsername(token.getToken());

```
this method "extractUsername()" will validate the token and return the email of the admin if the token is valid or else it will throw one of those exceptions depending on the case.

```
public String extractUsername(String token) throws
 ExpiredJwtException, UnsupportedJwtException, MalformedJwtException, SignatureException, IllegalArgumentException
    
```

## How to get the token:
you need to interact wiht the admin service to login -> send a post request to this endpoint https://admin-service-api.onrender.com/login
whith body containing the admin credintials 
```
{
"email":"admin@fawry.com",
"password":"123456"
}

```

and you will receive a response envelop like this
```
{
  "success": true,
  "data": {
    "token": "eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJhZG1pbkBmYXdyeS5jb20iLCJpYXQiOjE2OTI2Mzg3OTIsImV4cCI6MTY5MjY0MjM5Mn0.yx676UmRqQ9KYqyJmXuXhPjKzGaf5GsBg-OZJKkaBwU"
  },
  "errorDetails": null
}
```

then you can consume the token and validate it without interacting with admin service for validation.
the token expires in 1 hour.
