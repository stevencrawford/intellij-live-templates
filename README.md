# Intellij Live Templates

A collection of [Live Templates for IntelliJ](https://www.jetbrains.com/help/idea/using-live-templates.html) used in my day-to-day Java development.

# Java

## Core

1. `record-require-non-null` - Record requireNonNull wrapper for properties

```
java.util.Objects.requireNonNull($Property$);
```

## Spring Boot

1. `spring-boot-controller` - Spring Boot Controller class

```
@org.springframework.web.bind.annotation.RestController
@org.springframework.web.bind.annotation.RequestMapping("/api")
@lombok.RequiredArgsConstructor
class $Name$Controller {

    @org.springframework.web.bind.annotation.GetMapping("/hello")
    public org.springframework.http.ResponseEntity<String> hello() {
        return org.springframework.http.ResponseEntity.ok("Hello World!");
    }
}
```

2. `spring-boot-service` - Spring Boot Service class

```
@org.springframework.stereotype.Service
@lombok.RequiredArgsConstructor
public class $Class$Impl implements $Class$ {

    $END$
}
```

3. `spring-boot-repo-crud` - Spring Boot CRUD Repository Service class

```
@org.springframework.stereotype.Repository
public interface $Name$Repository extends org.springframework.data.repository.CrudRepository<$Name$, $Id$> {}
```

# Lombok

1. `lombok-data-class` - A simple Lombok @Data class with builder

```
@lombok.Builder
@lombok.Data
@lombok.AllArgsConstructor
@lombok.NoArgsConstructor
class $name$ {
    
    $END$
}
```

## Testing (JUnit)

1. `junit-test-method` - JUnit `@Test` method using Given / When / Then naming convention

```
@org.junit.jupiter.api.Test
public void given$Given$_when$When$_then$Then$() throws Exception {
    // arrange
    $END$
    
    // act
    
    // assert
}
```

2. `junit-assert-throws` - Assert that a specific Exception & Message are thrown.

```
org.assertj.core.api.Assertions.assertThatThrownBy(() -> $FunctionCall$)
                .isInstanceOf($ExceptionClass$.class)
                .hasMessageContaining($ExpectedMessageContent$);
```

3. `mock-type-with-annotation` - Annotation driven Mockito mocking of a given type 

```
@org.mockito.Mock
private $TargetType$ $fieldName$;
```

4. `mock-type` - Declarative Mockito of a given type

```
$TargetType$ $fieldName$ = org.mockito.Mockito.mock($TargetType$.class);
```

## Testing (REST-assured)

1. `rest-assured-get` - Sample GET request with assertions

```
io.restassured.RestAssured.given()
    .header("", "")
    .when()
    .get("/api/$PATH$")
    .then()
    .statusCode(200)
    .body("id", org.hamcrest.Matchers.notNullValue())
;
```

2. `rest-assured-post` - Sample POST request with assertions

```
io.restassured.RestAssured.given().contentType(io.restassured.http.ContentType.JSON)
    .body("""
          $BODY$
        """
    )
    .header("", "")
    .when()
    .post("/api/$PATH$")
    .then()
    .statusCode(201)
    .body("id", org.hamcrest.Matchers.notNullValue())
;
```

## Testing (MockMvc)

1. `mockmvc-test-class` A skeleton test class for a given Controller class

```
@org.springframework.boot.test.autoconfigure.web.servlet.WebMvcTest($NAME$Controller.class)
public class $NAME$ControllerMockMvcTest {

    @org.springframework.beans.factory.annotation.Autowired
    private org.springframework.test.web.servlet.MockMvc mockMvc;
    
}
```

2. `mockmvc-perform-get` A GET request with jsonPath assertions

```
mockMvc.perform(org.springframework.test.web.servlet.request.MockMvcRequestBuilders.get("/$PATH$"))
        .andDo(org.springframework.test.web.servlet.result.MockMvcResultHandlers.print())
        .andExpect(org.springframework.test.web.servlet.result.MockMvcResultMatchers.status().isOk())
        .andExpect(org.springframework.test.web.servlet.result.MockMvcResultMatchers.content().contentType("application/json"))
        .andExpect(org.springframework.test.web.servlet.result.MockMvcResultMatchers.jsonPath("$.id").value(org.hamcrest.CoreMatchers.is("some-value")));
;
```

3. `mockmvc-perform-post` A POST request with JSON Body

```
mockMvc.perform(org.springframework.test.web.servlet.request.MockMvcRequestBuilders.post("/$PATH$")
                .contentType("application/json")
                .content("""
                            {
                            }
                            """))
        .andDo(org.springframework.test.web.servlet.result.MockMvcResultHandlers.print())
        .andExpect(org.springframework.test.web.servlet.result.MockMvcResultHandlers.status().isNoContent())
;
```

## Testing (Cucumber)

1. `given-cucumber-step` - Cucumber @Given step definition method

```
@io.cucumber.java.en.Given("$step_pattern$")
public void $method_name$($params$) {
    $END$
}
```


## Spring OAuth

1. `spring-oauth-config-yaml` - Spring OAuth YAML configuration

```yaml
spring:
  security:
    oauth2:
      client:
        registration:
          $Provider$:
            client-id: $clientId$
            client-secret: $clientSecret$
        provider:
          $Provider$:
            authorization-uri: https://$yourIdpDomain$/oauth2/v1/authorize
            token-uri: https://$yourIdpDomain$/oauth2/v1/token
            user-info-uri: https://$yourIdpDomain$/oauth2/v1/userinfo
            jwk-set-uri: https://$yourIdpDomain$/oauth2/v1/keys
```

# AI Prompts

TODO: Add more
