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
> A distributed system is nothing more than multiple entities that talk to one another in some way, while also performing their own operations....Just as long as all the
> processes in a system are both autonomous, or capable of performing their own operations, while also able to communicate with other processes in the system, we can classify
> the system as being distributed.
*Source: https://medium.com/baseds/many-nodes-one-distributed-system-9921f85205c4*


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
> -- <cite>[james nunns][1]</cite>

[1]: https://techmonitor.ai/what-is/what-is-a-node-4927877#:~:text=A%20node%20is%20a%20device%20or%20data%20point%20in%20a%20larger%20network.&text=In%20networking%20a%20node%20is,or%20printer%20are%20considers%20nodes.

It's important to mention that a node is autonomous, meaning it can function on its own. If it's a piece of software it can run this software without need for other dependencies from other nodes.


### 1.2 What is a (micro)service?
To answer this question I used the literature study method as well as the community one.

#### Literature study:
Let's first explain what a service is. A service is something you would typically build with software in a distributed system, the service grants you a part of functionality. A service could also act like a node in a distributed system. Or as Wikipedia describes it:
> In the contexts of software architecture, service-orientation and service-oriented architecture, the term service refers to a software functionality or a set of softwar
> functionalities (such as the retrieval of specified information or the execution of a set of operations) with a purpose that different clients can reuse for different
> purposes, together with the policies that should control its usage (based on the identity of the client requesting the service, for example).
> -- <cite>[Wikipedia][2]</cite>

[2]: https://en.wikipedia.org/wiki/Service_(systems_architecture)

You might already guess it, a micro service is like a smaller service. Actually it's a one function service, therefore small, micro. A micro service is in fact part of the microservice architecture and the somewhat the opposite of a monolithic architectur. The microservice architecture consists of a lot of separate microservices fulfilling a job together. I'll give a quick context about monolithic architecture to explain microservices better. 

A monolothic arhitecture means that all your dependencies and software for your application, are together in one build. An article from Ivy Wigmore on TechTarget explains it as the following:
> Monolithic software is designed to be self-contained; components of the program are interconnected and interdependent rather than loosely coupled as is the case with modular
> software programs. In a tightly-coupled architecture, each component and its associated components must be present in order for code to be executed or compiled.
> -- <cite>[Ivy Wigmore][2]</cite>

[2]: https://whatis.techtarget.com/definition/monolithic-architecture#:~:text=A%20monolithic%20architecture%20is%20the,composed%20all%20in%20one%20piece.&text=In%20a%20tightly%2Dcoupled%20architecture,to%20be%20executed%20or%20compiled.

Let's talk about an example, if we wanted to build a basic calculator. We have functionalities like dividing and subtracting. In a monolithic application you would have these functionalities bundled together into one application. So when subtracting 5 from 2, this application will go to its designated method to do this and give the answer. But in a microservices architecture for example, we would have a seperate service for subtracting and another one for dividing. So dividing 10 by 5 would mean the application that takes care of the UI(front-end) will ask the micro service responsible for dividing for help. In this case it'll probably be a little bit too much, to create seperate micro services.

<br>

#### Community research:






<br>

## 2. How do services inside a distributed systems communicate with each other?

### 2.1 What types of communication are there?(async vs sync)
### 2.2 What protocol do these services use?
### 2.3 Why do services need to be able to communicate?

<br>

## 3. Why is it important that communication is happening safely?

### 3.1 How to test if the communication is secured?
