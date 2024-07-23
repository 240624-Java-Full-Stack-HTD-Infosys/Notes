## Spring / Spring Boot
 - @Autowired
 - @SpringBootApplication
 - @ComponentScan
 - @AutoConfiguration
 - @Configuration
 - @Bean
 - @Value
 - @Qualifier
 - @NoRepositoryBean
 - @Lazy
 - @Scope

## Spring Component Scanning Stereotypes
 - @Component - generic one
 - @Repository - specific
 - @Controller - specific
 - @Service - specific
 - @RestController - implies @Controller, so it works the same

## Spring Web
 - @RequestMapping - used to map a path to a handler (behavior/method to handle this request)
   - @GetMapping
   - @PostMapping
   - @PutMapping
   - @DeleteMapping
 - @RequestBody - Tells spring to take the body of the request and create an object based on that representation
 - @ResponseBody - Applied to the return type of a handler method, takes an object and coverts it into a resource represenation that is stored in the body of the response
 - @PathVariable (path parameters) - get a path param from the URI, a parameter which exists at a position in the URI
 - @RequestParam (query parameters) - similar to above, but the key/values are in the parameter list portion of the URI which comes after the '?'
     - www.site.com/something/path/to/something?key1=value1&key2=value2
 - @ResponseStatus - sets the status code in the response
 - @RestController - implies @Controller and @ResponseBody
 - @ExceptionHandler - similar to the RequestMappings, maps a thrown exception to another behavior designed to handle that scenario

## Spring Data JPA
 - @Transactional - Controls the behavior of transactions, specifically isolation, and transaction propagation. Sets the boundaries of the work, maintaining the hibernate session until the work is complete. Committing all of the work atomically when complete.
 - @Query

## Models/Entities - Jakarta Persistence Annotations
 - @Table
 - @Entity
 - @Column
 - @Id
 - @GeneratedValue
 - @OneToMany
 - @OneToOne
 - @ManyToMany
 - @ManyToOne
 - @JoinColumn
 - @JoinTable
 - @OrderBy
 

## JSR-303 Validators (also applied to models/entities)
 - @Pattern
 - @Min
 - @Max
 - @Range
 - @Length
 - @NotNull
 - @NotEmpty
 - @Email
 - @URL
 - @Past
 - @Future
 - @Digits
 - @DecimalMin
 - @DecimalMax
 - many more...
