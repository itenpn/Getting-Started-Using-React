---
name: "Getting Started Using React"
description: "A collection of information about React.js"
author: "Nicholas Iten"
group: "React"
order: 1
---

#Getting Started Using React

**Table of contents:**
- [I Installing React](#installing-react)
- [II First Steps With React](#first-steps-with-react)
- [III Making Your Website Appear on Screen](#making-your-website-appear-on-screen)
- [IV Creating React Components](#creating-react-components)
- [V Using JSX](#using-jsx)
- [VI How to use CSS](#how-to-use-css)
- [VII Using Props](#using-props)
- [VIII Using State](#using-state)
- [IX General React Tips](#general-react-tips)
- [X Finishing Your Website](#finishing-your-website)


## Installing React

1. Download the latest version of [Node.js](https://nodejs.org/en/download/)
2. Navigate to the terminal. Every operating system is different.
3. Install react using npm
   ```
   $ npm install --save-dev react
   $ npm install --save-dev react-dom
   ```
4. Navigate to a new Directory
  ```
  $ mkdir MyWebsite
  $ cd MyWebsite
  ```
5. Create a new project
  ```
  $ npx create-react-app [Project Name goes here]
  $ cd [Project name]
  $ npm start
  ```
6. A new localhost window should pop up with the default project


## First Steps With React

1. Open project folder using code editor
 - I recommend [VSCODE](https://code.visualstudio.com/download), but anything will do
2. Go to the public directory
3. Edit the index.html file
 - Inside `<head>` create a `<title>` for the website
 - Add new [fonts](https://fonts.google.com/) if needed
4. Change the favicon
 - Replace the favicon.ico with your own
 - [X-Icon](http://www.xiconeditor.com/) can make any image a favicon!
 - This may take a little while to update on localhost
5. Go to the src directory
6. Delete everything in the src directory, or you can just modify the files if you would like.


## Making Your Website Appear on Screen

1. Create an index.js file in the src directory
  - Import these two modules
  ```javascript
  import React from ‘react’;
  import ReactDOM from ‘react-dom’;
  ```
  - Import any relevant components from your src folder
  - Proper practice is to import an App.js file that has a render() for all of your components
  ```javascript
  import {App} from ‘./App.js’;
  ```
2. Render your project
  ```javascript
  ReactDOM.render(<App />, document.getElementById(‘root’));
  ```
  - `<App />` is a component that displays your website
  - `<App />` can be changed to any component that is created in index.js, or is imported
3. Now you can start creating your project!


## Creating React Components

1. Create a new JS file and its corresponding CSS file
  ```
  ComponentName.js
  ComponentName.css
  ```
2. Go to the JS file
  - First lines are always
  ```javascript
  import React from 'react';
  import './ComponentName.css';
  ```
  - Import other components from other files if necessary
3. Create a new class
  - I’ll use App.js as an example
  ```javascript
  export class App extends React.Component{
    
    //All classes must have a render() function
    render(){
      //You can use control statements to change the return value
      //render() can only return one JSX tag, use <div> to nest tags
      return(
        <div></div>
      );
    }
    
  }
  ```
4. Now you have a brand new component!
5. To import the component to another file
  - In the new file
  ```javascript
  import {ComponentName} from ‘./ComponentName.js’;
  ```
5. To use the component in another file
  - In the new `render()` use `<ComponentName />` as its JSX


## Using JSX

1.JSX is like HTML you can use inside of React Components
  - Every `render()` must return a single JSX tag, so use `<div>` to nest your HTML
2. Some things are different from HTML
  - `class` is a reserved word in JS, so you must use `className` instead
  - The `style` attribute must be passed a JS object, more on that in [How to Use CSS](#how-to-use-css)
3. You can insert JS code into JSX tags!
  - Wrap the variable around curly braces `{}`
  - Works for attributes and inner HTML!
4. You can insert Components with JSX
  - Just use `<ComponentName />`


## How to use CSS

1. Import the appropriate CSS file
  ```javascript
  import ‘ComponentName.css’;
  ```
2. Go to the CSS file
  - CSS operates just like normal, you can target `id`, `className`, and JSX tags
3. Inline styles are DIFFERENT IN REACT
  - Create a JS object
  ```javascript
  let style = {};
  ```
  - Add a CSS style, but without the hyphens and using camelCase
  - Example: 
  ```javascript
  let style = {fontSize: "10px"};
  ```
  - Add a comma at the end of the CSS style if you want to add another
  ```javascript
  let style = {fontSize: '10px', color: 'blue'};
  ```
  - To add an inline style, pass the object to the style attribute
  - Example with style variable: 
  ```javascript
  <h1 style={style}>Hello World</h1>
  ```
  - Example with new object: 
  ```javascript
  <h1 style={{color: ‘blue’}}>Hello World</h1>
  ```


## Using Props
1. Props stands for properties, they are how we can parameter pass with React
2. Any JS code can become a prop
  - Functions, variables, etc
3. Props allow us to communicate to other components
  - Ex: tell a picture w/ caption component to render a certain picture and give it a caption
4. Props are easy to use
  ```javascript
  <ComponentName prop1=[some data] prop2=[some data] />
  ```
  - Ex: 
  ```javascript
  <Photo picture={JohnDoePicture} caption=’John Doe, Manager’ />
  ```
5. To gather information from props use: `this.props.propName`
  - Ex: 
  ```javascript
  <img src={this.props.picture} />
  ```


## Using State

1. State tells React when to update a website
  - Anytime state changes, `render()` is called
  - Use states to change the design of your Component
2. To set an initial state, you must add a constructor
  ```javascript
  constructor(props){
    super(props);
    this.state = {};
  }
  ```
  - Inside of the curly brackets above, create a JS object like normal
3. To change a state, you must use this.setState()
  ```javascript
  this.setState({});
  ```
  - You can pass an object that only changes one state of the component
4. To change a state within JSX, you must use methods
  - Create a method within the class
  ```javascript
  methodName(e){  // you can add more data with methodName(e, data1, data2, etc...
    e.preventDefault(); //prevents the method from running without an event
    this.setState({
      //add state(s) here
    });
  }
  ```
  - Proper practice is to name the function handleEvent, where Event is what activates the function
  - Ex: `handleClick`
  - To allow this to work, you have to add another line to your constructor
  ```javascript
  this.methodName = this.methodName.bind(this);
  ```
5. This method can then be attached to events
  - Events trigger when an action occurs
  - onClick, onHover, etc
  - Ex: 
  ```javascript
  <button onClick={this.handleClick}>
  ```
6. To pass additional parameters with the method, you must use a function
  ```javascript
  (e) => {this.methodName(e, data)}
  ```
  - Ex: 
  ```javascript
  <button onClick={(e) => {this.handleClick(e, pageNum)}}>
  ```


## General React Tips

1. Any changes to a program must be changed using state
  - This includes things such as input boxes or forms
2. Use a singular App component that displays all of your pages depending on state
  - Use if statements to return different components in your render() function
3. Plan out your project design BEFORE you write code
  - This helps you stay organized and creates a common theme
4. You can add your own backend code to your React Website
  - Because everyone has a different preference, I will leave this up to you to figure out on your own, but this [tutorial](https://codeburst.io/creating-a-full-stack-web-application-with-python-npm-webpack-and-react-8925800503d9) starts you off on how to add python to react.


## Finishing Your Website

1. Create a new repository on [github](https://github.com/)
2. If you are on Windows, install [git](https://git-scm.com/downloads)
3. Open the terminal
4. Go to your project directory
```
$ cd MyWebsite\ProjectName
```
5. Create a new build
```
$ npm run build
```
6. Enter the following commands to add your code to github
```
# If you haven’t used git before, it will ask you to sign in,
# so do that when it gives you prompts instead of going to the next step.
$ git init
# The period is NOT a typo
$ git add .
$ git commit -m “First Commit”
# Go to github and copy the repository url
$ git remote add origin [Repository URL]
$ git remote -v
$ git push origin master
```
7. Now you have your code all on github!
8. Create an account at [Netlify](https://www.netlify.com/)
  - Link your account with the github repository and upload the \build folder
  - Now your website should run on Netlify!
9. To add a custom domain
  - Go to a domain registrar like [GoDaddy](https://www.godaddy.com/)
  - Buy a domain name.
  - Insert the custom domain name in Netlify, it will give you several DNS server links
  - On your domain registrar website, go to the DNS server option and link the server links.
  - Wait for a while and your custom domain should now work!
10. Celebrate!
