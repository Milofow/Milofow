to mock the behavior of a request made without really making a request to the url you can mock the behavior of a incoming request

to do that initialize the class as a @springboottest and @AutoconfigureMockMvc the latter will configure everything needed to mock the behavior of the controller to perform something you have to create a mockvc like this ```@Autowiredprivate MockMvc mockMvc```, this works fine if the controller has no dependencies but if you're using a service you need to also mock the dependency with the ```@MockBean``` annotation you need to use mockito for this annotation


source: https://spring.io/guides/gs/testing-web/
