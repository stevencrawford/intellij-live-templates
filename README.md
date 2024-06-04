# Intellij Live Templates

A collection of [Live Templates for IntelliJ](https://www.jetbrains.com/help/idea/using-live-templates.html) used in my day-to-day development across Java and Typescript. 

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
public void given$Given$_when$When$_then$Then() {
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

# Typescript

## NestJS

1. `nestjs-module` - NestJS Module class

```
import { Module } from '@nestjs/common';

@Module({
  imports: [],
  controllers: [],
  providers: [],
})
export class $MODULE_NAME$Module {}
```

2. `nestjs-service` - NestJS Service class

```
import { Injectable } from '@nestjs/common';

@Injectable()
export class $SERVICE_NAME$Service {

    constructor(
        $END$
    ) {
    
    }
}
```

# AI Prompts

TODO: Add more
