# jwt-validator-jar

## How to use:
you just need to add this jar into your dependencies and include it your pom.xml file 
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
