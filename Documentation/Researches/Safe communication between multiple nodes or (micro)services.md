# Security research regarding the communication between an amount of services or nodes.
Current semester we have to work with distributed systems, it's my first time working this way. Because I'm interested in creating safe systems, I'm going to dig into the safety while communicating between these systems. So I'm not only learning how to build distributed systems, but also learning how to secure the way they talk to each other.

## Research questions
### Main research question  
My main question that I want answered is:
* #### How to ensure a safe communication between multiple nodes/services?  

<br>

### Sub research questions
I will be answering the main question through the next sub questions:
* #### 1. What is a distributed system?
  * ##### 1.1 What is a node?
  * ##### 1.2 What is a service?
* #### 2. How do services inside a distributed systems communicate with each other?
  * ##### 2.1 What types of communication are there?(async vs sync)
  * ##### 2.2 What protocol do these services use?
  * ##### 2.3 Why do services need to be able to communicate?
* #### 3. Why is it important that communication is happening safely?
  * ##### 3.1 How to test if the communication is secured?



## DOT research methods
To make sure I get a reliable and valid outcome on this research, I used the following research methods:  

**Library:**
  * Literature study
  * Available product analysis (possible)
  * Best good and bad practices (possible)
  * Community research (possible)
  * Expert interview (possible)

**Field:**
  * Problem analysis (possible)
 
**Lab:**
  * Computer simulation (possible)
  * Data analytics (possible)
  * Security test (possible)

**Workshop:**
  * Decomposition (possible)
  * Multi-criteria decision making (possible)




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



## 2. How do services inside a distributed systems communicate with each other?

### 2.1 What types of communication are there?(async vs sync)
### 2.2 What protocol do these services use?
### 2.3 Why do services need to be able to communicate?

<br>

## 3. Why is it important that communication is happening safely?

### 3.1 How to test if the communication is secured?
