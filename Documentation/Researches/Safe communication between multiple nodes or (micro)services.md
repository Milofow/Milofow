# Security research regarding the communication between an amount of services or nodes.
Current semester we have to work with distributed systems, it's my first time working this way. Because I'm interested in creating safe systems, I'm going to dig into the safety while communicating between these systems. So I'm not only learning how to build distributed systems, but also learning how to secure the way they talk to each other.

## Research questions
### Main research question  
My main question that I want answered is:
* #### How to ensure safe communication between nodes/services?  

<br>

### Sub research questions
I will be answering the main question through the next sub questions:
* #### 1. What is a distributed system?
  * ##### 1.1 What is a node?
  * ##### 1.2 What is a (micro)service?
* #### 2. How does communication work inside a distributed system?
  * ##### 2.1 What types of communication are there?
  * ##### 2.2 What protocols do they use?
  * ##### 2.3 Why do services need to be able to communicate?
* #### 3. Where to secure communication?
  * ##### 3.1 Are distributed systems more vulnerable to security threats?
  * ##### 3.2 How to test if communication is secured?



## DOT research methods
To make sure I get a reliable and valid outcome on this research, I used the following research methods:  

**Library:**
  * Literature study

**Lab:**
  * Security test (Future implementation)




<br>




## 1. What is a distributed system?
It's actually exactly what it says, a system that is distributed over multiple places. In this context we're talking about distribution of software systems that are working apart from each other, maybe even at a reasonable distance from one another. An additional definition from an article on splunk:

> A distributed system is a computing environment in which various components are spread across multiple computers (or other computing devices) on a network. These devices split
> up the work, coordinating their efforts to complete the job more efficiently than if a single device had been responsible for the task. 
> Distributed systems are an important development for IT and computer science as an increasing number of related jobs are so massive and complex that it would be impossible for
> a single computer to handle them alone.
> -- <cite>[splunk][1]</cite>



They appoint typical characteristics of a distributed system as the following:

> - **Scalability:** The ability to grow as the size of the workload increases is an essential feature of distributed systems, accomplished by adding additional processing units
> or nodes to the network as needed.
> - **Concurrency:** Distributed system components run simultaneously. They’re also characterized by the lack of a “global clock,” when tasks occur out of sequence and at
> different rates.
> - **Availability/fault tolerance:** If one node fails, the remaining nodes can continue to operate without disrupting the overall computation.
> - **Transparency:** An external programmer or end user sees a distributed system as a single computational unit rather than as its underlying parts, allowing users to interact
> with a single logical device rather than being concerned with the system’s architecture.
> - **Heterogeneity:** In most distributed systems, the nodes and components are often asynchronous, with different hardware, middleware, software and operating systems. This 
> allows the distributed systems to be extended with the addition of new components.
> - **Replication:** Distributed systems enable shared information and messaging, ensuring consistency between redundant resources, such as software or hardware components, 
> improving fault tolerance, reliability and accessibility.
> -- <cite>[splunk][1]</cite>

[1]: https://www.splunk.com/en_us/data-insider/what-are-distributed-systems.html.


A distributed system usually contains of nodes or (micro)services. That's why I have two sub questions to answer to know what I'm dealing with. Read on further for an explanation on these terms.

If you want some more in depth information about this topic, I recommend reading [this article](https://www.freecodecamp.org/news/a-thorough-introduction-to-distributed-systems-3b91562c9b3c/)

<br>

### 1.1 What is a node?
I found a great explanation from james nunns on Tech Monitor that explains it really well and even in multiple contexts.
> A node is a device or data point in a larger network.
> 
> A node can be a couple of different things depending on whether the conversation is about computer science or networking.
> 
> In networking a node is either a connection point, a redistribution point, or a communication endpoint. In computer science, nodes are devices or data points on a large
> network, devices such a PC, phone, or printer are considers nodes.
> 
> In general, a node has a programmed or engineered capability that enables it to recognise, process, or forward transmissions to other nodes.
> -- <cite>[james nunns][2]</cite>

[2]: https://techmonitor.ai/what-is/what-is-a-node-4927877#:~:text=A%20node%20is%20a%20device%20or%20data%20point%20in%20a%20larger%20network.&text=In%20networking%20a%20node%20is,or%20printer%20are%20considers%20nodes.

It's important to mention that a node is autonomous, meaning it can function on its own. If it's a piece of software it can run this software without need for other dependencies from other nodes.


### 1.2 What is a (micro)service?
Let's first explain what a service is. A service is something you would typically build with software in a distributed system, the service grants you a part of functionality. A service could also act like a node in a distributed system. Or as Wikipedia describes it:
> In the contexts of software architecture, service-orientation and service-oriented architecture, the term service refers to a software functionality or a set of softwar
> functionalities (such as the retrieval of specified information or the execution of a set of operations) with a purpose that different clients can reuse for different
> purposes, together with the policies that should control its usage (based on the identity of the client requesting the service, for example).
> -- <cite>[Wikipedia][3]</cite>

[3]: https://en.wikipedia.org/wiki/Service_(systems_architecture)

You might already guess it, a micro service is like a smaller service. Actually it's a one function service, therefore small, micro. A micro service is in fact part of the microservice architecture and the somewhat the opposite of a monolithic architectur. The microservice architecture consists of a lot of separate microservices fulfilling a job together. I'll give a quick context about monolithic architecture to explain microservices better. 

A monolothic arhitecture means that all your dependencies and software for your application, are together in one build. An article from Ivy Wigmore on TechTarget explains it as the following:
> Monolithic software is designed to be self-contained; components of the program are interconnected and interdependent rather than loosely coupled as is the case with modular
> software programs. In a tightly-coupled architecture, each component and its associated components must be present in order for code to be executed or compiled.
> -- <cite>[Ivy Wigmore][4]</cite>

[4]: https://whatis.techtarget.com/definition/monolithic-architecture#:~:text=A%20monolithic%20architecture%20is%20the,composed%20all%20in%20one%20piece.&text=In%20a%20tightly%2Dcoupled%20architecture,to%20be%20executed%20or%20compiled.

Let's talk use an example, if we wanted to build a basic calculator. We have functionalities like dividing and subtracting. In a monolithic application you would have these functionalities bundled together into one application. So when subtracting 5 from 2, this application will go to its designated method to do this and give the answer. But in a microservices architecture for example, we would have a seperate service for subtracting and another one for dividing. So dividing 10 by 5 would mean the application that takes care of the UI(front-end) will ask the micro service responsible for dividing for help. In this case it'll probably be a little bit too much, to create seperate micro services.



<br>



## 2. How does communication work inside a distributed system?
In order for the services/nodes to work together they need to communicate, this happens by sending messages to each other. These messages contain responses or demands from other services. Through messages is not the only way they can work together, it's also possible to let services work event based or with requests to each other. This explanation is very simple and a little bit vague. While implementing this there is a lot more to it, but it gives us a clear starting point.

Now we know something about communication, but what about where to communicate to or from? What if we have a front end that wants to talk to all these services, instead of them talking to each other. We can adress all services seperately from the front end, or we can put a broker in between that handles all our messages. The broker acts like a postman delivering them to the designated services.

<br>

### 2.1 What types of communication are there?
We can split all types of communication into two categories: synchronous and asynchronous. 

#### Synchronous
> Basically, we can say that Synchronous communication is using HTTP or gRPC protocol for returning sync response. The client sends a request and waits for a response from the
> service. So that means client code block their thread, until the response reach from the server.
> -- <cite>[Mehmet Özkaya][5]</cite>

[5]: https://medium.com/design-microservices-architecture-with-patterns/microservices-communications-f319f8d76b71

#### Asynchronous
> Asynchronous protocol. In this case, the sub-processes are not locked and protocols that are compatible with many operating systems and cloud environments are used. One
> example would be the AMQP protocol, where the client’s or message sender’s code usually does not wait for a reply. What is does is simply send a message to a RabbitMQ queue or
> any other messaging agent.
> -- <cite>[Chakray][6]</cite>

[6]: https://www.chakray.com/microservices-communication-methods-types-and-styles/


<br>
<br>


The next are the most popular ways of communicating inside a distributed system:

* #### HTTP communication
In several articles and videos the first thing discussed is HTTP communication. It's also the most popular and works pretty good, this option is mostly used synchronous. It works by sending requests to other services and expects a response from them. The article I read from [embitel](https://www.embitel.com/blog/ecommerce-blog/how-microservices-communicate-with-each-other) has to say the following:
> HTTP has the total control while choosing how services should communicate with each other. HTTP calls between services is a feasible approach for service-to-service
> communication.

Synchronous
> In such cases when one service is dependent on another service, the services complete their task cycle and then meet the requests received from another service. This is called
> Synchronous HTTP calls between services. There is no coupling between services here. But those services that placed requests have to wait till they get the response, in order
> to perform any action.

Asynchronous
> HTTP asynchronous call is another option between two services. Here, the service takes request from the first service in case of multiple requests and immediately responds
> with a URL. This URL is used to check on the progress of the request. The services need not wait for their response as this happens instantly as coupling is loose. The
> services are isolated.

<br>

* #### Message communication
The [same article](https://www.embitel.com/blog/ecommerce-blog/how-microservices-communicate-with-each-other) has a good compact description about this way of communicating:
> In message communication, the participating services do not communicate directly with each other. The services push messages via message broker in order to reach out to other
> services. The message broker is the point of contact between all services. This reduces complexity and increases efficiency.
> 
> However, there is still some coupling between services using this approach. Both or all the services must agree on the message structure and components involved before the
> workflow.

As you might have seen this approach is asynchronous as well as the next one.

<br>

* #### Event-driven communication
This communication is almost the same as the message one, but doensn't communicate with messages. Its main way of communicating is listening to events from other services, these events arrive as a message that services respond to. The article from [embitel](https://www.embitel.com/blog/ecommerce-blog/how-microservices-communicate-with-each-other) says: 
> An event-driven pattern is another asynchronous approach where coupling between services is completely removed. In an event-driven approach the services need not know about
> any common message structure. Communication happens through events that individual services generate.
> 
> A message broker is still needed here as individual services will write their events to it. However, the participating services need not know the details of the event. They
> only respond to the event that is happening and not any message that the event would deliver.

<br>

#### Sources
* https://www.embitel.com/blog/ecommerce-blog/how-microservices-communicate-with-each-other


### 2.2 What protocols do they use?
I'm going to divide them into two ways of communication: HTTP and message communication. Message and event-driven work more or less the same in my opinion, they both use the same way but listen and react to different things. I only focus on the popular ones, because there are simply to many.

#### HTTP/HTTPS communication
HTTP itself is actually a protocol, it's a protocol used to send requests to a service in order to receive a respone. These responses are normally formatted in a special way. This way is now a days JSON but could also be XML. 


* ##### REST and SOAP
REST and SOAP are both used for sending requests over HTTP. I'm not going into depth about SOAP, because it's less and less used today. But REST is very popular, it's a way of sending requests that makes it easier for services to talk to each other. An article on codecademy explains REST as:
> REST, or REpresentational State Transfer, is an architectural style for providing standards between computer systems on the web, making it easier for systems to communicate
> with each other. REST-compliant systems, often called RESTful systems, are characterized by how they are stateless and separate the concerns of client and server
> -- <cite>[codecademy][7]</cite>

[7]: https://www.codecademy.com/article/what-is-rest


<br>


#### Message communication
Some of these protocols require a broker to communicate with. Most of the time this works with a pubsub system. An explanation given by Auri Poso on Aiven is:
> The pub-sub communication method is an elaboration on this latter method. The sender merely sends events — whenever there are events to be sent— and each receivers choose,
> asynchronously, which events to receive.
> -- <cite>[Auri Poso][8]</cite>

[8]: https://aiven.io/blog/how-are-your-microservices-talking

<br>

* ##### AMQP
> Asynchronous protocols like AMQP use a lightweight service bus similar to a service-oriented architecture (SOA) bus, though much less complex. Unlike HTTP, this bus provides a
> message broker that acts as an intermediary between the individual microservices, thus avoiding the problems associated with a brokerless approach.
> -- <cite>[Clive Longbottom][9]</cite>

[9]: https://searchapparchitecture.techtarget.com/tip/Styles-protocols-and-methods-of-microservices-communication

You can use this protocol with brokers like Kafka or RabbitMQ

<br>

* ##### gRPC
> It is focused on high performance and uses the HTTP/2 protocol to transport binary messages. It is relies on the Protocol Buffers language to define service contracts.
> Protocol Buffers, also known as Protobuf, allow you to define the interface to be used in service to service communication regardless of the programming language.
> -- <cite>[Mehmet Özkaya][10]</cite>

[10]: https://medium.com/design-microservices-architecture-with-patterns/microservices-communications-f319f8d76b71

According to his article it works like:
> In GRPC, a client application can directly call a method on a server application on a different machine like it were a local object, making it easy for you to build
> distributed applications and services.
> -- <cite>[Mehmet Özkaya][11]</cite>

[11]: https://medium.com/design-microservices-architecture-with-patterns/microservices-communications-f319f8d76b71

Because gRPC works binary, meaning it's data is transfered with zeros and ones, it's much faster than human readable requests and responses. Therefore it's more used in the back end services because a readable response isn't necessary. It also doesn't require a broker, it works more like a HTTP request.

<br>

* ##### GraphQL
> GraphQL can be defined as a declarative query language, syntax, and a runtime that is used to request data on a server. It provides a comprehensive and understandable
> description of the data in your API, thereby providing clients with the ability to define and ask for exactly what they want and nothing more or less. With the power to make
> specific requests, it becomes easier for developers to evolve APIs over time and utilize more robust tools. GraphQL is agnostic to how your data is stored in the backend and
> it offers a collective type-safe layer of all the data sets in your server.
> -- <cite>[RapidAPI][12]</cite>

[12]: https://rapidapi.com/blog/api-glossary/graphql/

<br>

##### Real-time communication
An addition to these methods is real-time communication, which is possible through the use of several brokers. A protocol you can use is Websockets, these are packages send to the client through a broker in real-time, meaning a very short time between the creation of something and showing it. This article from Microsoft gives a little bit more context to possibilities:
> SignalR is a good way to achieve real-time communication for pushing content to the clients from a back-end server. Since communication is in real time, client apps show the
> changes almost instantly. This is usually handled by a protocol such as WebSockets, using many WebSockets connections (one per client). A typical example is when a service
> communicates a change in the score of a sports game to many client web apps simultaneously.
> -- <cite>[Microsoft][13]</cite>

[13]: https://docs.microsoft.com/en-us/dotnet/architecture/microservices/architect-microservice-container-applications/communication-in-microservice-architecture

<br>

### 2.3 Why do services need to be able to communicate?
If you choose to build your application on microservice architecture you probably already know the answer to this one. But I still wanted to adress this to make it full circle. The microservice architecture is build on separating everything, thus creating a demand for services who sometimes depend on other services' logic to talk someway. Let's give an example, if we order something on a webshop it'll probably have a order service, product service, cart service, etc. That order service has to deal with products so it needs to communicate with the product service. You could do this to communicate everything back to the front-end, but it would defeat the whole purpose of microservices, as well as being very inefficient en overcomplicated.



<br>


## 3. Where to secure communication?
I found a lot of possibilities, two articles described a lot of measures to take clearly. I'll quote some places where to secure a distributed system.

* #### Do everything over HTTPS
While reading articles all over the web I found one saying to work over HTTPS:
> You should use HTTPS everywhere, even for static sites. If you have an HTTP connection, change it to an HTTPS one. Make sure all aspects of your workflow—from Maven
> repositories to XSDs—refer to HTTPS URIs.
> -- <cite>[Matt Raible][14]</cite>

[14]: https://developer.okta.com/blog/2020/03/23/microservice-security-patterns

HTTPS encrypts your request meaning people can intercept the request or respone but can't decrypt it nor read it.

<br>

* #### Access and identity tokens
> In microservices deployment, a large number of applications and services will require secure authorization and access control. An authorization framework such as the OAuth 2.0
> and OpenID enables you to process the tokens securely, hence protect your microservices. Consequently, this allows third-party applications to access other services or data
> from users.
> 
> In a typical deployment, the main application will prompt the user to authorize the third party service. Upon accepting this, the application generates an access token for the
> session.
> -- <cite>[Amos Kingatua][15]</cite>

[15]: https://geekflare.com/securing-microservices/

This way you can restrict who can succesfully make calls to your services.

<br>

* #### Service to service security
> Generally, there are three main techniques that you can use to secure the interservice communications. These are the Trust the network, JSON Web Token (JWT), and Mutual
> Transport Layer Security (mTLS, or Mutual TLS). 
>
> Out of the three, the most popular is the mTLS. In this approach, each microservice must carry a public/private key pair. The client microservice then uses the key-pair to
> authenticate itself to the receiving microservice through the mTLS.
> -- <cite>[Amos Kingatua][16]</cite>

[16]: https://geekflare.com/securing-microservices/

This looks somewhat the same as the tokens, but a technique I did not know was possible in microservices.

<br>

* #### API gateway
> Generally, the microservices consist of several components distributed over different networks and accessible from a wide range of systems and clients. Exposing the\
> microservices increases vulnerabilities and security risks. One way to protect them is to create a single and secure entry point that helps you to centralize all access from
> external systems and clients.
> 
> To achieve this, deploy an API gateway to screen all incoming requests for security issues before routing them to the appropriate microservices. The API gateway sits between
> the client applications and the microservices. It then limits exposing the microservices while providing additional request management functions such as authentication, SSL
> termination, protocol translation, monitoring, request routing, caching, and more.
> -- <cite>[Amos Kingatua][17]</cite>

[17]: https://geekflare.com/securing-microservices/

<br>

* #### Secure docker environment
> Most often, microservices rely on container technology. As such, securing the containers, both internally and externally, is one way of reducing the attack surface and the
> risks.
> -- <cite>[Amos Kingatua][18]</cite>

[18]: https://geekflare.com/securing-microservices/

<br>

* #### Slow down attackers
> If someone tries to attack your API with hundreds of username and password combinations, it will likely take a while for them to authenticate successfully. Slowing down this
> process even more is another way to protect your various endpoints. Using an approach like rate limiting, for instance, means that attackers can only make one or two attempts
> per second, which may deter them from continuing credential stuffing attacks on your systems.
> -- <cite>[Okta][19]</cite>

[19]: https://www.okta.com/resources/whitepaper/8-ways-to-secure-your-microservices-architecture/


### 3.1 Are distributed systems more vulnerable to security threats?
A lot of articles talk about the risk being higher compared to a monolithic system, because of much more entrypoints to secure. An example from an article is:

> A significant security consideration when choosing between a monolith and microservices is the number and size of attack surfaces. An attack surface is the sum of
> vulnerabilities in an application — the smaller it is, the better. In a monolith, there is only one attack surface, albeit a sizable one. With microservices, however, each
> service has its own attack surface, but of lesser size.
> -- <cite>[Thomas Bush][20]</cite>

[20]: https://nordicapis.com/which-is-more-secure-monolith-or-microservices/

But another article also has to mention advantages to a micro service architecture:
> They say microservices architecture is better security-wise as the functions can be tested separately. However, this technology might be a drawback as it is. Let us explain.
> Each microservice has a separate API, they are easily adjusted and reconfigured not bothering the whole app. It will be running despite one or two services being down at the
> moment. It is undoubtedly good. What’s worse is that each microservice also has a number of APIs and ports thus making an app prone to intrusions.
> -- <cite>[Lambda Test][21]</cite>

[21]: https://www.lambdatest.com/blog/does-microservices-architecture-influence-security-testing/


So to answer the question, it depends on how many services you have and how well you secure it. But on large systems, I think it's way more vulnerable than a monolithic application. 


### 3.2 How to test if communication is secured?
Start by acting like an attacker and try to communicate with API's through unexpected ways. This article has some good points as well:
> This stage uses web application attacks, such as cross-site scripting, SQL injection and backdoors, to uncover a target’s vulnerabilities. Testers then try and exploit these
> vulnerabilities, typically by escalating privileges, stealing data, intercepting traffic, etc., to understand the damage they can cause.
> 
> Rules For Api Security Testing
> 
> An API should provide expected output for a given input.
> The inputs should appear within a particular range and values crossing the range must be rejected.
> Any empty or null input must be rejected when it is unacceptable.
> Incorrectly sized input must be rejected.
> -- <cite>[Harry Davis][22]</cite>

[22]: https://quick-adviser.com/what-are-the-methods-to-perform-security-testing-on-microservices/


<br>


## Conclusion
This research tells you something about what a distributed system is, but also what protocols the intercommunication might use and where their advantages are. If you do good research on what protocol is best for you, you already are one step closer to providing a good secure architecture. Beside that we also can look at multiple ways to secure your communication and work towards an overall good level of securiness. The only way to know for sure is to test your safety measures, for now it's hard to say how to do this. In the future I'd like to make a proof of concept and test it for real, but for now this research will provide enough information.
