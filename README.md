# Portfolio Milo Timmermans

## Introduction
I'm Milo Timmermans and I'm currently studying ICT software engineering at Fontys Hogescholen. This is my beginning of my personal portfolio, that's gonna start with some learning outcomes that I'll have to proof to complete semester 3 of my study. The learning outcomes that need to be achieved are listed below and overtime will be expanded.




## Start of the project
To help me prove some of the learning outcomes I'll be making a project. It will be a IoT dashboard, more information can be found in its repo [here](https://github.com/Milofow/front-end-dashboard)

#### C4
It will be my first time working with distributed systems, therefore I started off easy with these simple architecture designs.
<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/73555911/148978923-fd1f4930-7726-4bdc-8f81-0b9cb801e02e.jpg" width=500 height=250></td> 
    <td><img src="https://user-images.githubusercontent.com/73555911/148978950-961de705-2ff4-426e-a451-b2c6ffec664c.jpg" width=500 height=250></td> 
  </tr>
 </table>
 
 Later on I improved them and made them more fitting to my project. The current architecture file can be found [here](https://github.com/Milofow/front-end-dashboard/blob/master/documentation/Architecture:%20C4.md)
 
![C4](https://user-images.githubusercontent.com/73555911/150020893-121dcb31-aa43-4d0c-88d3-708a4da42924.gif)

 
#### User Stories
To specify what I had to make I created User stories, they can be found here: [User Stories](https://github.com/Milofow/front-end-dashboard/blob/master/documentation/User%20stories.md)


#### Front-end
I've chosen to get to know the React framework to create my front-end. I've chosen React because it's a popular framework and a lot of my peers are currently working with it, which makes asking for help a lot easier.



#### Back-end
Previous semester I worked with C# language for the back-end, because I like to know a bit of everything I've chosen Java for my backend, due to Java being a new language for me. My next search was for a good framework and I stranded with the popular Spring framework. We had a workshop about Java frameworks and the host was very excited about Spring, his excitement was contagious.






## Learning Outcomes

### Outcome 1. You design and build user-friendly, full-stack web applications.

##### 1. Identity service: Login, Register and account information service with 0Auth2
I first started off with a login system for my project. I used Auth0 as it works very well and is easy to implement, because of it's good documentation.

![Auth0](https://user-images.githubusercontent.com/73555911/147069214-461c915e-80d1-4cdd-9d13-1fd7956068d2.gif)


##### Sources
- https://www.youtube.com/watch?v=MqczHS3Z2bc
- https://auth0.com/docs/quickstart/spa/react


##### 2. MQTT
Here I build a simple form for sending a message to services subscribed to the topic 'presence', to get a little bit known with how mqtt works. I'm using websockets to send the data to the MQTT broker and it sends it back to the console. The MQTT broker I'm using is Mosquitto.
<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/73555911/142778419-c3f36e67-2fbe-425b-ae89-df1d5d518d63.png" width=500 height=250></td> 
    <td><img src="https://user-images.githubusercontent.com/73555911/142778454-6641c44f-4ec8-418e-b13c-96c66247359c.png" width=500 height=250></td> 
  </tr>
 </table>


##### Sources
- http://www.steves-internet-guide.com/mqtt-websockets/


##### 3. API Devices service
Because this semester is about distributed systems I created a separate API service for handling this which can be found [here](https://github.com/Milofow/devices-service)

##### Sources
- https://www.youtube.com/watch?v=y8IQb4ofjDo&list=PLqq-6Pq4lTTZSKAFG6aCDVDP86Qx4lNas&ab_channel=JavaBrains


##### 4. Discovery service
Because I was following JavaBrains's course, I created a discovery service that detects running services. This could come in handy if I was using more or back up services.





I did not implement the discovery service later on, because my circumstances did not ask for a discovery service, thus it being needless.


##### Sources
- https://www.youtube.com/watch?v=y8IQb4ofjDo&list=PLqq-6Pq4lTTZSKAFG6aCDVDP86Qx4lNas&ab_channel=JavaBrains




### Outcome 2. You use software tooling and methodology that continuously monitors and improve the software quality during software development.

#### 1. Unit and integration testing
With Spring boot it's really simple to write tests, with the `@SpringBootTest` annotation you can run the entire server and test like it's a real server. But Spring also provides Mockito and it's almost the same thing but it doesn't require the server to start, but mocks its behavior instead. This makes testing quicker and it doesn't depend on external factors like a database. 

Here you can see one of those tests that mimics the behavior of a real request and expects certain outcomes.
![image](https://user-images.githubusercontent.com/73555911/149328098-aa5c6383-875a-4037-b3a3-020efa327a24.png)

I also wrote a little research on these kind of tests which can be found here: [MockMvc Spring testing](https://github.com/Milofow/S3-Portfolio/blob/main/Research/MockMvc%20Spring%20testing.md)
Sources:

#### 2. Automated tests on push
To ensure a good software management system I want to run my tests on certain Github actions I perform. Like pushing to development from a feature branch, I would like to check if my tests are still passing, because if they aren't I may pushed something to development that isn't even working.

As you can see in the image below I merged a feature branch into development after the PR. It runned all the tests and the passed.
![image](https://user-images.githubusercontent.com/73555911/149326354-cbf9376e-b995-4d49-8e7a-568942b0cf31.png)


##### Sources
- 

#### 3. Testing with H2 database

Sources:

#### 4. Exception testing

Sources:

#### 5. Code review


### Outcome 3. You design and implement a (semi)automated software release process that matches the needs of the project context.

#### 1. Docker containers
Continuously delivery needs a way to deliver my product to the outside world, therefore I invested Docker because docker runs in its own environment making it very easy to run it elsewhere and spread your product. To create a docker from your project you'll need a dockerfile, this file has all the steps it needs to create a docker instance so it can run everywhere. It mostly tells what dependencies it needs and how to create a final build to deploy. 

My dockerfiles can be found here:
[Device service](https://github.com/Milofow/devices-service/blob/master/Dockerfile)
[Dashboard front end]()

##### Sources
- https://docs.docker.com/


#### 2. Deploy web services

##### Sources


### Outcome 4. You act in a professional manner during software development and learning.

#### 1. Project board
To start working more user story oriented I started a project board on Github. Mainly being the reason I needed some planning and what better place to do it, where my project was living, Github. I put all my user story with a short text on it, so I can start working from there. I use this board with the front end repo aswell as the back end repo.

![Project board](https://user-images.githubusercontent.com/73555911/148846433-2c75a89f-bc5c-48de-a19e-09c929491d60.png)




#### 2. Github flow
To add a little bit more of professionalism, as a preparation for the future. I try working with the so called Github flow. This means having seperate branches, for seperate stages in your project. Because the project isn't to big I will be working with the flow as it's explained in the picture below:

![image](https://user-images.githubusercontent.com/73555911/148848367-a49769a0-739f-4366-8399-f56265434b78.png)
<i> Source: https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow </i>


#### 3. Researches
[MQTT research](https://github.com/Milofow/S3-Portfolio/blob/main/Research/MQTT.md)
[Security research regarding the communication between an amount of services or nodes.](https://github.com/Milofow/S3-Portfolio/blob/main/Research/Safe%20communicating%20between%20multiple%20nodes.md)


