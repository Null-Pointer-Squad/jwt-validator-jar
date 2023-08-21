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
