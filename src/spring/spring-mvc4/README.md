# spring-mvc starter project

  - Spring 4
  - Spring Boot
  - Jackson

# Credits

- https://app.pluralsight.com/library/courses/spring-mvc4-introduction

# Build

  - `mvn clean install -U`
  - Package as `war` and drop into Tomcat

# Commentary

### com.pluralsight

  - Configuration classes go here
  - We register a `DispatcherServlet`, upon which Spring MVC runs
  - We add route mappings for `*.html`, `*.pdf`, `*.json`
  - We load in our configuration class, `com.pluralsight.WebConfig`
  - Our WebConfig uses the `@Configuration` and `@EnableWebMvc` annotations
  - WebConfig tells spring to begin a scan of all packages under `com.pluralsight`
  - We set the default locale to English
  - We tell spring to listen out for the qs 'language'. If one is entered, use the value to set a new locale
  - We register an `InternalResoureViewResolver` with the paths and extension of our view files
  - We register two static file paths, `/pdf/` and `/css/`

### com.pluralsight.controller

  - Controller classes are given the `@Controller` annotation
  - Controller methods are mapped to a route with the `@RequestMapping` annotation, which can also specify a HTTP verb
  - Controller methods take in a Model class (which is automatically sent to the view)
  - Controller methods return the name of the view to render
  - Validation results can be passed into Controller methods with the `BindingResult` class
  - When returning a view name, redirect clears and state and forward retains it
  - API controllers are given the `@RestController` annotation
  - In our example, the `.json` extension is used for JSON responses

### com.pluralsight.model

  - Model classes are POJOs
  - Model classes are given validation annotations, such as `@NotEmpty`
  - A custom validator is used, `@Phone`

### com.pluralsight.view

  - Custom validation classes are kept here, along with associated validation annotations

### src/main/webapp/WEB-INF

  - Views (`.jsp`), css, static files go here
  - This location is registered with the web application in the `WebConfig` class