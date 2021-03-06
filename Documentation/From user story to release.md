# From user story to release
In this document I will be showing a work process that is centered around a user story.

## 1. User story
First I'm going to create a user story that is related to my application. I'm going to create a simple one, like showing all my devices when I login.
<table>
  <thead>
    <tr>
      <td><b>Title:</b> <br>1. Overview of my devices</td>
      <td><b>Priority:</b> <br> 5/5</td>
      <td><b>Estimate:</b> <br> 3h</td>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td colspan="3">
        <b>User Story:</b><br> 
        <b>As</b> a smart home owner, <br>
        <b>I want</b> to see all my devices grouped together on a dashboard, <br>
        <b>so that</b> I can control them more easily.</td>
    </tr>
    <tr>
      <td colspan="3">
        <b>Acceptance Criteria:</b><br>
          <ul>
            <li>I only want to access my devices after I'm logged in</li>
            <li>I want to see the device's name</li>
            <li>I want to see the device's status</li>
            <li>I want to be able to control them from this overview</li>
            <li>If no devices are available I want to see this on my dashboard</li>
          </ul>
        </td>
    </tr>
  </tbody>
</table>



## 2. Project board
When I'm finished with the user story I'm going to create issues related to that user story. I need to fulfill these issues to come closer to implementing the user story. I like to put the issues on the project board on Github. In the end it'll look like this:
![Project board](https://user-images.githubusercontent.com/73555911/150214003-1750f910-7017-4dc0-92e3-47033b073b20.png)

## 3. Feature branch
Because we're going to implement new features, I start by making a new branch for the issue `US 2 - Dashboard only accesisable when logged in #17`. I call the branch for the front end something similair like `US2-Access-dashboard-when-logged-in` and start working on it. For the back end I created the branch called `US2-Get-all-devices
`.


## 4. Implement
Now I'm going to write the code for this issue on the designated branch. I started off with the back end and implemented the controller with the service getting all the devices. 




## 5. Testing
I wrote two implementation test, one for the happy flow and one for the bad one:
![Integration tests](https://user-images.githubusercontent.com/73555911/150333206-4bc2b90f-0e23-42c5-83ed-db085e03fce9.png)




## 6. Release
Now that we implementend a (part) of the user story, we can release it to master. First we push the working code with tests to the designated branch. After I make a pull request for this branch. I work with the github flow that this images describes:
<img src="https://i.postimg.cc/rwwdRDGc/Github-flow.png" width="485"/>


* ### Pull request
![image](https://user-images.githubusercontent.com/73555911/150332125-fbc55cb3-0794-49e0-8564-9a36e98a70c7.png)


