# Portfolio Milo Timmermans

## Introduction
I'm Milo Timmermans and I'm currently studying ICT software engineering at Fontys Hogescholen. This is my beginning of my personal portfolio, that's gonna start with some learning outcomes that I'll have to proof to complete semester 3 of my study. The learning outcomes that need to be achieved are listed below and overtime will be expanded.




## Start of the project
To help me prove some of the learning outcomes I'll be making a project. It will be a IoT dashboard, more information can be found in its repo [here](https://github.com/Milofow/front-end-dashboard)

* ### C4
To start of with implementing seperate services I first created some designs to get me started. This will be my first time working with distributed systems, therefore I started off easy with these simple architecture designs.
<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/73555911/148978923-fd1f4930-7726-4bdc-8f81-0b9cb801e02e.jpg" width=500 height=250></td> 
    <td><img src="https://user-images.githubusercontent.com/73555911/148978950-961de705-2ff4-426e-a451-b2c6ffec664c.jpg" width=500 height=250></td> 
  </tr>
 </table>
 
Later when I had a better understanding of this distributed architecture, I improved it by creating a real C4 model. It's pretty acurate to my project and my future plans. The full architecture diagrams can be found [here](https://github.com/Milofow/front-end-dashboard/blob/master/documentation/Architecture:%20C4.md)
 
![C4 diagrams](https://user-images.githubusercontent.com/73555911/150020893-121dcb31-aa43-4d0c-88d3-708a4da42924.gif)

<br>
 
* ### User Stories
To specify what I had to make I created User stories, they can be found in the project's repo here: [User Stories](https://github.com/Milofow/front-end-dashboard/blob/master/documentation/User%20stories.md). Later on I improved them by doing research on them and they start looking like the one on the right

<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/73555911/150345639-cd9dc210-a2c9-4d00-b962-654a83e6bb75.png"></td> 
    <td><img src="https://user-images.githubusercontent.com/73555911/150345832-1917a526-554a-4310-8bae-ee53fd93fa03.png"></td> 
  </tr>
</table>



* ### Front-end
I've chosen to get to know the React framework to create my front-end. I've chosen React because it's a popular framework and a lot of my peers are currently working with it, which makes asking for help a lot easier. Because it's so popular there is a lot of documentation, which makes it great for learning.


* ### Back-end
Previous semester I worked with C# language for the back-end, because I like to know a bit of everything I've chosen Java for my backend, due to Java being a new language for me. My next search was for a good framework and I stranded with the popular Spring framework. We had a workshop about Java frameworks and the host was very excited about Spring, his excitement was contagious.



<br>



## Learning Outcomes

### Outcome 1. You design and build user-friendly, full-stack web applications.

#### 1. Identity service: Login, Register and account information service with 0Auth2
I first started off with a login system for my project. I used Auth0 as it works very well and is easy to implement, because of it's good documentation.

![Auth0](https://user-images.githubusercontent.com/73555911/147069214-461c915e-80d1-4cdd-9d13-1fd7956068d2.gif)


##### Sources
- https://www.youtube.com/watch?v=MqczHS3Z2bc
- https://auth0.com/docs/quickstart/spa/react

<br>

#### 2. MQTT
Here I build a simple form for sending a message to services subscribed to the topic 'presence', to get a little bit known with how mqtt works. I'm using websockets to send the data to the MQTT broker and it sends it back to the console. The MQTT broker I'm using is Mosquitto.

<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/73555911/142778419-c3f36e67-2fbe-425b-ae89-df1d5d518d63.png"></td>  
  </tr>
 </table>


##### Sources
- http://www.steves-internet-guide.com/mqtt-websockets/

<br>

#### 3. API Devices service
Because this semester is all about distributed systems, I created a separate API service for handling this which can be found [here](https://github.com/Milofow/devices-service)

This is what my controller looks like for handling requests with methods like get, put, delete and post.
![IntelliJ](https://user-images.githubusercontent.com/73555911/150022513-292db6f8-251f-4f65-a627-8c88ff71a2b6.png)

<br>

You can make simple requests, we can test this with postman, that looks like:
![API GET request](https://user-images.githubusercontent.com/73555911/150023264-27a7c8de-34c1-4f4d-9a2d-bdfed4b248e8.gif)


##### Sources
- https://www.youtube.com/watch?v=y8IQb4ofjDo&list=PLqq-6Pq4lTTZSKAFG6aCDVDP86Qx4lNas&ab_channel=JavaBrains

<br>

#### 4. Discovery service
Because I was following JavaBrains's course, I created a discovery service that detects running services. This could come in handy if I was using more or back up services.

![image](https://user-images.githubusercontent.com/73555911/150024022-b78f5def-8c6f-461b-917d-62f69cbd3b35.png)


In the end I did not implement the discovery service later on, because my circumstances did not ask for a discovery service, thus it being needless.


##### Sources
- https://www.youtube.com/watch?v=y8IQb4ofjDo&list=PLqq-6Pq4lTTZSKAFG6aCDVDP86Qx4lNas&ab_channel=JavaBrains

<br>

### Outcome 2. You use software tooling and methodology that continuously monitors and improve the software quality during software development.

#### 1. Unit and integration testing
With Spring boot it's really simple to write tests, with the `@SpringBootTest` annotation you can run the entire server and test like it's a real server. But Spring also provides Mockito and it's almost the same thing but it doesn't require the server to start, but mocks its behavior instead. This makes testing quicker and it doesn't depend on external factors like a database. 

Here you can see one of those tests that mimics the behavior of a real request and expects certain outcomes.
![image](https://user-images.githubusercontent.com/73555911/149328098-aa5c6383-875a-4037-b3a3-020efa327a24.png)

I also wrote a little research on these kind of tests which can be found here: [MockMvc Spring testing](https://github.com/Milofow/S3-Portfolio/blob/main/Research/MockMvc%20Spring%20testing.md)

<br>

#### 2. Automated tests on push
To ensure a good software management system I want to run my tests on certain Github actions I perform. Like pushing to development from a feature branch, I would like to check if my tests are still passing, because if they aren't I may pushed something to development that isn't even working.

As you can see in the image below I merged a feature branch into development after the PR. It runned all the tests and the passed.
![image](https://user-images.githubusercontent.com/73555911/149326354-cbf9376e-b995-4d49-8e7a-568942b0cf31.png)

<br>

#### 3. Code review
In our group project we did a lot of code reviews. I did reviews and others did reviews on my code. This way you can get a fresh opinion on your code and someone else might notice something you don't.

<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/73555911/150350127-25e63ef9-2dfd-48bf-afe9-0bae30ce2503.png"></td>  
    <td><img src="https://user-images.githubusercontent.com/73555911/150350277-c2b2ba66-5da2-4bed-ac5d-6c0c9bc3ed3b.png"></td>  
  </tr>
 </table>


<br>


### Outcome 3. You design and implement a (semi)automated software release process that matches the needs of the project context.

#### 1. Docker containers
To start of with working with containers, I chose Docker because it has great documentation and is widely used, therefore I can find a lot of tutorials about it. It works pretty simple it only need a dockerfile, this file has all the steps it needs to create a docker instance so it can run everywhere. It mostly tells what dependencies it needs and how to create a final build to deploy. 

My dockerfiles can be found here:
[Device service](https://github.com/Milofow/devices-service/blob/master/Dockerfile)
[Dashboard front end](https://github.com/Milofow/front-end-dashboard/blob/master/Dockerfile)


##### Sources
- [Docker docs](https://docs.docker.com/)

<br>

#### 2. Deliver to Docker hub
Continuously delivery needs a way to deliver my product to the outside world, therefore I invested Docker because docker runs in its own environment making it very easy to run it elsewhere and spread your product. It wraps my project into a docker using the docker file and finally pushing it to docker hub with version. Down below you can see the succeeded workflow that when pushed to master branch, it will deliver to docker hub. 


<table>
  <tr>
    <td><img src="https://user-images.githubusercontent.com/73555911/150348776-4841656a-c08f-401b-9b59-3b281e5389b6.png"></td>  
    <td><img src="https://user-images.githubusercontent.com/73555911/150349051-44e0874e-5cd2-4ffb-8e71-bf393a2729db.png"></td>  
  </tr>
 </table>
 
 
##### Sources
- [Docker docs](https://docs.docker.com/)

<br>

### Outcome 4. You act in a professional manner during software development and learning.

#### 1. Project board
To start working more user story oriented I started a project board on Github. Mainly being the reason I needed some planning and what better place to do it, where my project was living, Github. I put all my user story with a short text on it, so I can start working from there. I use this board with the front end repo aswell as the back end repo.

![Project board](https://user-images.githubusercontent.com/73555911/148846433-2c75a89f-bc5c-48de-a19e-09c929491d60.png)

<br>

#### 2. Github flow
To add a little bit more of professionalism, as a preparation for the future. I try working with the so called Github flow. This means having seperate branches, for seperate stages in your project. Because the project isn't to big I will be working with the flow as it's explained in the picture below:

![image](https://user-images.githubusercontent.com/73555911/148848367-a49769a0-739f-4366-8399-f56265434b78.png)
<i> Source: https://www.atlassian.com/git/tutorials/comparing-workflows/gitflow-workflow </i>

<br>

#### 3. Researches

* ##### User stories
Because I stumbled upon making good user stories, I wanted to broad my knowledge around creating a good story. For this project and all the others to come, that's why I decided to do the following research about it:
[**How to create a good user story?**](https://github.com/Milofow/S3-Portfolio/blob/main/Documentation/Researches/How%20to%20create%20a%20good%20user%20story%3F.md)

* ##### Safe distributed communication
Semester 3 is all about distributed systems, because of that I wanted to write a research about communication in such a system, and most important how this can happen safely. This research can be found here:
[**Safe communication between multiple nodes or (micro)services.**](https://github.com/Milofow/S3-Portfolio/blob/main/Documentation/Researches/Safe%20communication%20between%20multiple%20nodes%20or%20(micro)services.md)


