
## Hooks
UseState = local variable to keep track of. practice const [message, setMessage] = useState("Hello React!")

UseEffect = something that happens on event but is not relatable to a component loading (animations, retrieving data)

The `useEffect` Hook is useful to perform additional work behind the scenes, without affecting the appearance of the webpage.

Example: 
``` UseEffect(() => {
  console.log('It's ${emotion} around here!');
}, [emotion (it listens for this value to change and if so it will console log the emotion)]);
```

UseReducer
One purpose of the `useReducer` Hook is to prevent hardcoding by encapsulating code that processes user input into a new function.


(source: https://www.linkedin.com/learning/react-js-essential-training/working-with-useeffect?contextUrn=urn%3Ali%3AlyndaLearningPath%3A593715e0498e9e9be7fb8506&u=2095956)


## functions & components



In javascript there are multiple ways to create a function. For example:
```
function myFunction () {
//some action
}
const myFunction = () => {
//some action
}
```
These two are functions and makes the same thing.

Now second part of your question is "What is the difference between functional and class based components?"

Class based components used for controlling your state and for lifecycle methods(ComponentDidMount and etc...) in the past. And if you are not using state in your component or lifecyle methods, you would use functional based component. Basically if you have a small component with only some UI things, it was best to use functional components. However with React version 16.8 React team intruduced hooks.

Hooks provides the same concepts with your state and component lifecyle methods and more. With hooks you can control your component even if they are funcitonal components.

(source: https://stackoverflow.com/questions/60338452/const-vs-class-functions-function-name-in-react-native)
