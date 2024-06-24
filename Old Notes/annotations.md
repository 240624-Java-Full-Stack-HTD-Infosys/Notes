# Core - Config & Beans
- **@SpringBootApplication** - Indicates to Spring this should adhere to Spring Boot autoconfig, by implying the following:
  - **@Configuration** or **SpringBootConfigration** - Spring boot specific configs
  - **@EnableAutoConfiguration** - also spring boot's opinionated configs
  - **@ComponentScan** - set up bean config method to be component scanning
- **@EnableTransactionManagement** - turns on transaction management infrastructure
- **@EnableAutoConfiguration**
- **@Autowired** - tells Spring where to  injects dependencies 
- **@Bean** - tells spring that the method marked produces a bean
- **@Configuration** - It indicates that a class provides bean definitions and configuration settings to the Spring application context. It's like a blueprint for how things should be set up in a Spring application.
- **@Component** - identifies a class definition as a generic Component to be scanned, instantiated, and injected with dependencies by Spring
- **@Service** - Service Components are the class file which contains @Service annotation. These class files are used to write business logic in a different layer.
- **@Controller** - a stereotype annotation that indicates that a particular class serves the role of a controller/web request handler.
- **@Repository** - a specialization of @Component to indicate that the class contains the mechanisms for storing, retrieving, updating, and deleting operations on a repository
- **@RestController** - marks class as RESTful controller; combines @Controller and @ResponseBody, automatically serializes the return value of a method to the HTTP response body.
- **@Value** - used to provide a scalar or literal value for injection into the property of a spring bean
- **@Scope** - used to define the scope of a bean, which determines the lifecycle and visibility of that bean in the contexts where it's used
- **@Qualifier** - used to specify which bean should be injected when there are multiple beans of the same type in the Spring container

# Web
 - **@EnableWebMVC**: This annotation enables default Spring MVC configuration and support and registers Spring MVC infrastructure components expected to process web requests. It is usually used in conjunction with @Configuration annotation and helps developers customize configurations
 - **@RequestMapping** - It is used in Spring MVC to map web requests to specific methods in a controller. It defines how an HTTP request should be handled by specifying the URI (Uniform Resource Identifier) and the HTTP method (GET, POST, etc.) that should trigger the method in the controller.
 - **@GetMapping** is used to map HTTP GET requests to a specific method in a Spring controller. This annotation is part of the Spring Web module, which provides features for building web applications.
 - **@PutMapping** - Used to create a put http request in the controller layer of a spring program. 
 - **@PostMapping** is used to map HTTP POST requests to a specific method in a controller. This annotation acts as a shortcut for @RequestMapping(method = RequestMethod.POST).
 - **@DeleteMapping**: This has the effect of mapping the HTTP DELETE web request to specific handler methods. It basically is the short version for @RequestMapping(method = RequestMethod.DELETE)
 - **@PathVariable** - marks a parameter in a method to be assigned the value given in the corresponding path variable
 - **@RequestParam** - marks a parameter in a controller method to be populated with the value associated with a key in the request payload
 - **@ResponseStatus** - specifies the status code of an HTTP response (as long as the marked method completes successfully)
 - **@RequestBody** - Marks a parameter as a request payload that should be de-serialized from JSON/XML. Maps the HttpRequest body to a transfer/domain object, enabling automatic deserialization of the inbound HttpRequest body onto the Java Object. 
 - **@ResponseBody** -  This annotation is added on to a controller method to indicate that the response of that method will be returned via the reponse body of an HTTP response. This annotation is implicit if one applies the @RestController annotation to the top of the class. 
 - **@RequestHeader**
 - **@ExceptinoHandler** - is used to define a method that handles a specific type of exception.

# Data
 - **@Transactional** - used to describe transaction propigation strategies. This should be placed on a class or method. To enable transaction management in Spring we use the @EnableTransactionManagement annotation
 - **@Query** is commonly used in the context of Spring Data JPA. The @Query annotation is used to define custom queries to be executed by a Spring Data JPA repository.
 - **@Id** - identifies the field of an Entity's class definition as the primary key
 - **@Column** - is used to define the properties of a column in a database table.
 - **@GeneratedValue** - This defines generation strategy for primary keys; strategies include Identity, Auto, Sequence and Table. Use looks like this: @GeneratedValue(strategy = GenerationType.IDENTITY)
   - IDENITY - indicates the database should automatically generate primary key when entity is persisted
   - AUTO - strategy decided by persistence provider (Hibernate)
 - **@Table** - defines table details for the table used to store entities in the database
 - **@OneToMany**
 - **@ManyToMany** - Used to specify a many to many link 2 between entities.
 - **@OneToOne** - This annotation is used on the field/attribute of an entity, in order to establish a one to one relationship with another entity. 
 - **@ManyToOne** -  used to create a many-to-one relationship between two entities.
 - **@JoinColumn** - used to specify the mapping of a foreign key column in a relationship between two entities.

# Unit Testing
- **@SpringBootTest**
- **@DataJpaTest**
- **@WebMvcTest**
- **@MockBean**

# AOP
- **@EnableAspectJAutoProxy** - turns on AspectJ infrastructure
- **@Around** - The post powerful type of advice
- **@Before**
- **@After**
- **@AfterReturning**
- **@AfterThrows**
- **@Aspect**
- **@JoinPoint**
- **@PointCut**
