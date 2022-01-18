# Mock Mvc
A good way to do an integration test in Spring Boot Mvc is to use Mock Mvc. The Mock Mvc simulates a request that's made from the outside but without actually making that request from the outside. This way you can test realistic behavior and you won't be needing your service to be active.

Dependencies: JUnit, Spring MockMvc and Mockito.

<br>

## @SpringBootTest
To start in it's simplest form you'll need the annotation the ```@SpringBootTest```.

> The ```@SpringBootTest``` annotation tells Spring Boot to look for a main configuration class (one with @SpringBootApplication, for instance) and use that to start a Spring 
> application context.

<i>Source: https://spring.io/guides/gs/testing-web/</i>

So for example you can start the whole environment with adding ```webEnvironment=``` and run your test like this:

```java
@SpringBootTest(webEnvironment = WebEnvironment.RANDOM_PORT)
public class Test {
  
  @LocalServerPort
  private int port;

  @Autowired
  private TestRestTemplate restTemplate;

  @Test
  public void requestShouldReturnString() throws Exception {
    assertThat(this.restTemplate.getForObject("http://localhost:" + port + "/",
    String.class)).contains("return from controller");
  }
}
```

But this is not mocking anything, that's because the SpringBootTest is behaving like a real server. In the next section we'll discuss this.

<br>



## @AutoConfigureMockMvc
To really start mocking we'll need the ```@AutoConfigureMockMvc``` annotation. This will tell Spring Boot we're using MockMvc and also inject it. So the example above will look like:


```java
@SpringBootTest
@AutoConfigureMockMvc
public class Test {
  
  @Autowired
  private MockMvc mockMvc;

  @Test
  public void requestShouldReturnString() throws Exception {
    this.mockMvc.perform(get("/path/to/controller/get/mapping")).andDo(print()).andExpect(status().isOk())
				.andExpect(content().string(containsString("return from controller")));
}
```
Now the server doesn't start while executing the test, but will mock the behavior instead.

<br>

## @WebMvcTest
You can replace both annotations above the class with ```@WebMvcTest``` to ensure only the web layer is tested (that's what we're trying to do here). To specify a specific controller to narrow it down you can use ```@WebMvcTest(YourController.class)```.

### @MockBean
To mock a dependency used inside a controller like a service, we can use the annotation to create and inject the mock for the service like:

```java
@Mockbean
private YourService service;
```



<i>Source: https://spring.io/guides/gs/testing-web/</i>
