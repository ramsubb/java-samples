package com.example.api;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.ResponseBody;

public interface MyApi {
    @GetMapping("/hello")
    @ResponseBody
    String hello(@RequestParam(value = "name", required = false) String name);
}

package com.example.controller;

import com.example.api.MyApi;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class MyApiController implements MyApi {

    @Override
    public String hello(String name) {
        return "Hello, " + (name != null ? name : "World") + "!";
    }
}


package com.example.config;

import io.swagger.v3.oas.models.OpenAPI;
import io.swagger.v3.oas.models.info.Info;
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;

@Configuration
public class SwaggerConfig {

    @Bean
    public OpenAPI customOpenAPI() {
        return new OpenAPI()
                .info(new Info().title("Spring Boot API")
                .version("1.0")
                .description("Spring Boot API Documentation"));
    }
}


<dependency>
    <groupId>org.springdoc</groupId>
    <artifactId>springdoc-openapi-ui</artifactId>
    <version>1.7.0</version>
</dependency>
<dependency>
    <groupId>org.springframework.boot</groupId>
    <artifactId>spring-boot-starter-web</artifactId>
</dependency>
