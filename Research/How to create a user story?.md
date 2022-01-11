# How to create a user story?
This question will be useful, because I've noticed that working with user stories is worth your while. 
Therefore I want to dig into it to prepare me for making excellent user stories in the future.

## What is a user story?
A user story is a great way to display your functionalities from the product you are developing. 
A user story tells what a certain person wants to do to achieve something or solve a problem. It's written as simple as possible with avoiding technical terms.

Another way to look at what a user story is, is from the next definition brought by Andrii Bondarenko in his article on [Stormotion](https://stormotion.io/blog/how-to-write-a-good-user-story-with-examples-templates/):
> User Story is a small (actually, the smallest) piece of work that represents some value to an end user and can be delivered during a sprint.

How is a user story different from a task? The image below explains the difference:
![Stories vs. Tasks](https://cdn.sanity.io/images/w4zc2lav/production/db8ae8d188f957d953b9653a0b7ecd2fe964fb5e-2429x1278.png?w=1920&h=1010&auto=format)
*Source: https://www.easyagile.com/blog/how-to-write-good-user-stories-in-agile-software-development/*
   
>  Tasks are about implementation; user stories are about definition.

*Source: https://www.theinnovationmode.com/the-innovation-blog/user-stories-in-agile-the-whys-and-hows*

## How to use user stories?
User stories are mainly used with scrum. You can fill your project's backlog with user stories and underlying tasks, because the user stories shoul be not too broad to take onto in one sprint, they are perfect for the sprint backlog.


## Why user stories?
User stories create a very specific task that needs to be done and can be defined done if the acceptance criteria is met. Making it very easy to work off the functions in your product. Because it is based on a persona you don't loose the connection with this person, making you keep the end user in mind. The tasks are normally small making them easy to finish and oversee what needs to be done. So it's a perfect starting point for figuring out what to do and allow space for discussions.



## How to form a user story?
A simple template to create a user story with, is the following:
> As < persona >,    
> I want < what? >  
> so that < why? >.
  
*Source: https://www.romanpichler.com/blog/10-tips-writing-good-user-stories/*

How can we use the template to form a user story:
> * "As a [persona]": Who are we building this for? We’re not just after a job title, we’re after the persona of the person. Max. Our team should have a shared
> understanding of who Max is. We’ve hopefully interviewed plenty of Max’s. We understand how that person works, how they think and what they feel. We have empathy
> for Max.
> * “Wants to”: Here we’re describing their intent — not the features they use. What is it they’re actually trying to achieve? This statement should be
> implementation free — if you’re describing any part of the UI and not what the user goal is you're missing the point.
> * “So that”: how does their immediate desire to do something this fit into their bigger picture? What’s the overall benefit they’re trying to achieve? What is the
> big problem that needs solving?

*Source: https://www.atlassian.com/agile/project-management/user-stories*

#### Example:
```As a new user, I want to sign up using my existing Google account so that I don't have to keep track of another account.```
*Source: https://www.nuclino.com/articles/user-story-template-examples*

### Persona
As they show in the template it's more of a persona then a user, because it could be anybody. 

> Personas are fictional characters that are based on first-hand knowledge of the target group. They usually consist of a name and a picture; relevant characteristics, behaviours, and attitudes; and a goal.

*Source: https://www.romanpichler.com/blog/10-tips-writing-good-user-stories/*

To start forming correct user stories you need to make sure you know this persona. As this piece of an article explains: 

> If you don’t know who the users and customers are and why they would want to use the product, then you should not write any user stories. Carry out the necessary
> user research first, for example, by observing and interviewing users. Otherwise, you take the risk of writing speculative stories that are based on beliefs and
> ideas—but not on data and empirical evidence.

*Source: https://www.romanpichler.com/blog/10-tips-writing-good-user-stories/*

#### Example:


### Acceptance criteria
Afer you're done creating a perfect user story you should start writing some acceptance criteria for it. These are the criteria you have to meet to ensure your user story is fulfilled. I also found a template for that one:

> Given that [some context], when [some action is carried out], then [a set of observable outcomes should occur].

*Source: https://www.aha.io/roadmapping/guide/requirements-management/what-is-a-good-feature-or-user-story-template*

I have to say that one is a little bit vague to me, so for now I like to just create a couple of bullet points with the criteria that needs to be met to have succesfully implemented the user story.

Not only think about functional tasks you'll have to complete to meet the acceptance criteria, there is more as this quote will tell:
> These criteria can be functional (identifying user tasks, functions or business processes), non-functional (design and UI-related) and performance criteria
> (related to performance metrics, for example, loading time).

*Source: https://hygger.io/blog/user-story-template-how-to-write-it/*

Acceptance criteria goals:
> to clarify what the team should build before they start work
> to ensure everyone has a common understanding of the problem/need of the customer
> to help team members know when the story is complete
> to help verify the story via automated tests

![Acceptance critertia tasks](https://cdn.sanity.io/images/w4zc2lav/production/4e4c1c47e06f8e2ebdeb90d65511e61d075fafc7-1839x1277.png?w=1839&h=1277&auto=format)

*Source: https://www.easyagile.com/blog/how-to-write-good-user-stories-in-agile-software-development/*

#### Example:
![Acceptance criteria example](https://www.altexsoft.com/media/2018/07/example-1.png)
*Source: https://www.altexsoft.com/blog/business/acceptance-criteria-purposes-formats-and-best-practices/*

To check if your user story is optimal formed you can check if it fits the next criteria which forms the acrnonym:
> **Independent** – they can be developed in any sequence and changes to one User Story don’t affect the others.  
> **Negotiable** – it’s up for the team to decide how to implement them; there is no rigidly fixed workflow.  
> **Valuable** – each User Story delivers a detached unit of value to end users.  
> **Estimable** – it’s quite easy to guess how much time the development of a User Story will take.  
> **Small** – it should go through the whole cycle (designing, coding, testing) during one sprint.  
> **Testable** – there should be clear acceptance criteria to check whether a User Story is implemented appropriately.  

*Source: https://stormotion.io/blog/how-to-write-a-good-user-story-with-examples-templates/

Now that we know something about creating them, lets think about these four points before we can start of.

> 1. Make up the list of your end users. Define what their “pain” or “need” is, which you’re trying to solve.
> 2. Define what actions they may want to take.
> 3. Find out what value this will bring to users and, eventually, to your product. Also ask yourself - will any party pay us for this?
> 4. Discuss acceptance criteria and an optimal implementation strategy.
   
*Source: https://stormotion.io/blog/how-to-write-a-good-user-story-with-examples-templates/*


## Sources
- https://www.romanpichler.com/blog/10-tips-writing-good-user-stories/







Don't make user stories just for the sake of it, really think about the additional value:
> If you can’t answer what value this feature brings to end users and your product as well, then you’re doing something wrong.

*Source: https://stormotion.io/blog/how-to-write-a-good-user-story-with-examples-templates/*
