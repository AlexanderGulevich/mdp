# SPRING


#### Spring application context
It creates and manages application components ( beans ) wired together inside the Spring application context
The act of wiring beans together is based on a pattern known as dependency injection(DI).
Rather than have components create and maintain the lifecycle of other beans that they depend on, application relies on a separate entity (the container) to create and maintain all components and inject those into the beans


#### Autowiring
Automatic configuration has its roots in the Spring techniques known as autowiring and component scanning. With component scanning, Spring can automatically discover components from an application’s classpath and create them as beans in the Spring application context. With autowiring, Spring automatically injects the components with the other beans that they depend on. More recently, with the introduction of Spring Boot, automatic configuration has gone well beyond component scanning and autowiring. Spring Boot is an extension of the Spring Framework that offers several productivity enhancements. The most well-known of these enhancements is autoconfiguration, where Spring Boot can make reasonable guesses of what components need to be configured and wired together, based on entries in the classpath, environment variables, and other factors.


#### Some of annotations
__@Component, @Service, @Repository__ --  declared for component scaning and creating instanse as a bean in context

__@SpringBootApplication__  It is composit if thee annotations

- @SpringBootConfiguration 
- @EnableAutoConfiguration
- @ComponentScan - lets to declare @Component/@Controller/@Service etc.



__@Slf4j__ - lombok-provided annotation that generate Logger


Annotation | Description
--|--
@RequestMapping |  General request handling
@GetMapping |  Handles HTTP GET requests
@PostMapping  | Handles HTTP POST requests
@PutMapping |  Handles HTTP PUT requests
@DeleteMapping |  Handles HTTP DELETE requests
@PatchMapping |  Handles HTTP PATCH requests


#### Controllers
The center of Spring MVC is a concept of controller as a class that handle requests and	responds data.
```java
@Controller
@RequestMapping("/orders")//specifies the kind of request 
@SessionAttributes("order")

public class OrderController {
  
  @GetMapping("/current")
  public String orderForm() {
    return "orderForm";
  }

  @PostMapping
  public String processOrder() {
    return "redirect:/";
  }
```

#### Tests


```java

@RunWith(SpringRunner.class)
//JUnit annotation providing test a runner that guide Junit.
//SpringRunner is a Spring-provided test runner.
//It is an alias for SpringJunit4ClassRunner
//and was introduced to remove associations with a specific version of JUnit.

@SpringBootTest
//load application context for tests
class TacoCloudApplicationTests {

	@Test
	void contextLoads() {
	}

}
```

```java
@RunWith(SpringRunner.class)
@WebMvcTest(HomeController.class)// special test annotation for spring mvc
public class HomeControllerTest {
	
	@Autowired //inject MockMVC
	private MockMvc mockMvc;
	@Test	
	public void testHomePage() throws Exception{
		mockMvc.perform(get("/"))// Performs GET
		.andExpect(status().isOk())// Expect HTTP 200
		.andExpect(view().name("home"))//Expect home view
		.andExpect(content().string(containsString("Welcome to ... ")));//find substring
	}
}
```

