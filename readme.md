# Intro to React.js

---

![react-logo](./images/react-white-logo.png)

---

## Learning Objectives

* Explain what a frontend framework is and why they can be helpful in writing more complex applications.
* Explain what ReactJS is and where it fits in our applications' stack.
* Explain the component model of web development.
* Create and render React components in the browser.

## Framing

### What is a Frontend Framework? (5 mins)

- A framework is software providing generic functionality that serves as foundation to build and deploy applications.
- A framework manages the overall application flow. Simply put, frameworks call the code you write while you call the code provided by a library.
- While dense, the introduction of the [software framework](https://en.wikipedia.org/wiki/Software_framework) article on wikipedia does an excellent job on an exact definition.
- The way that Sinatra and Rails are frameworks that run on the server, receiving incoming request from the client, preforming some work that you have defined, and returning some response to the client, a front end framework runs in the client's browser (meaning in what language?), receives input from interactions with the page, performs some work that you have defined, and makes any updates necessary.
- There are [many](http://stateofjs.com/2016/frontend/) front end frameworks and each go about solving problems of how state is managed, updated, and represented by a view but there are many commonalities.
- There is a lot of debate over whether frontend frameworks count as frameworks at all -- some people say that they are just libraries and should be referred to as such.

### What is ReactJS? (10 mins)

React is a JavaScript library used to craft modern day UI and views for the front-end in web applications.

> **Selling Point:** By modeling small compatible components that focus on just rendering a view, we can move business logic out of the DOM, and therefore improve our app's performance, maintainability, modularity and readability.

#### Some History 

The first thing most people hear about React is "Facebook uses it."
* First used by Facebook in 2011.
* Then Instagram in 2012.
* Went open source in May 2013.

React was born out of Facebook's frustration with the traditional MVC model and how..
  * Re-rendering something meant re-rendering everything (or just a lot).
  * That had negative implications on processing power and ultimately user experience, which at times became glitchy and laggy.

> If you want to get a taste of what React is all about, [here's an introduction from React.js Conf 2015](https://www.youtube.com/watch?v=KVZ-P-ZI6W4&feature=youtu.be&t=510). Recommend starting around the 8:35 mark and watching until 16:30.

### React in MVC

React can be thought of as the "Views" layer.

React will work with any back-end language, but for project 3 and in our in-class examples we will be using Mongoose and Express for the models and controllers.

<details>
  <summary><strong>What is the role of a "view" in a front-end Javascript application?</strong></summary>
  The visual template the user sees, often populated with data from our models.
</details>
---

### Exercise: Thinkster RealWorld Applications (10 minutes / 5 minutes review)
* With the other people at your table, look at the code on the RealWorld ToDo repository [here](https://github.com/gothinkster/realworld). This site shows the same to do list application written in a bunch of different front end frameworks.
* For this exercise, look at the VanillaJS and React examples on their site.
* With your neighbor, discuss what differences you see between the React code and the vanilla JavaScript code. Write down your findings on the table next to you.


## Components (5 mins)

One of the snarky comments made about React when it was first open sourced was. "Rethinking established best practices". Traditionally we're used to a more MVC approach for separation of concerns. In React, we want to move towards more of a component-based separation of concerns.

When taking a look at Facebook, you could think of each status post as a mini-component in React. And a list of those updates, is a component that contains several of those mini-components. You could take that one step further and think of the Facebook app, as one giant component with several components within it. (Things like the list of status updates, the friends list, the header, etc...)

Imagine you worked at Facebook when they wanted to shift from using likes to reactions. Using traditional JavaScript, HTML, and CSS the shift would make you have to change your code in a bunch of places. Component based architecture allows us to maintain our code more easily.


### You Do: Identifying Components (10 minutes)

> 5 minutes exercise. 5 minutes review.
* Break into groups of three and take a look at Facebook. Identify the visual "components" the website is comprised of. We suggest using markers to draw these out on your table! So something like this...

![Component diagram](https://maketea.co.uk/images/2014-03-05-robust-web-apps-with-react-part-1/wireframe_deconstructed.png)

As you're drawing this out, think about the following questions...
* Where do you see "nested components"? Where do you not?
* Are there any components that share the same structure?
* Of these similar components, what is different about them?


### [F.I.R.S.T. Components](https://addyosmani.com/first/)

A React component is built to expect an input and render a UI with it. More importantly, a well-structured component only receives data specific to its purpose. For example, our `Post` component from the blog example will only receive `title`, `author` and the like as inputs -- nothing else.

This is because React follows a more **functional** approach to programming. For React components under this approach, **the same input will always produce the same output**.

You can build an app in a lot of ways, but if you want to look at some of the best practices, we can talk about what a component should be: **F.I.R.S.T.**

#### Focused

Components should do one thing and do it well.

#### Independent

Components should increase cohesion and reduce coupling. Behavior in one component should not impact the behavior of another. In other words, components should not rely on one another.

> But they should compliment one another.

#### Reusable

Components should be written in a way that reduces the duplication of code.

#### Small

Ideally, components should be short and condensed.

#### Testable

Because the same input will always produce the same output, components are easily unit testable.

> If you're interested, [Jest](https://facebook.github.io/jest/docs/tutorial-react.html) is a popular testing library for React.

---
### Break: 10 minutes

## Initial Setup (20 minutes)

In order to create a new project and to get our development environment setup, we are going to use the Terminal command `create-react-app`. It will create a new folder in your current directory for the in-class application.

`create-react-app` is an NPM package also built by Facebook that writes our build dependencies for us so that we can do less configuration. It allows us to use React, JSX, and ES6. It also allows us to import our CSS, it autoprefixes our CSS so that we don't have to worry about cross browser compatibility, it gives us a dev server to run, and it enables hot reloading which updates the code in our browser without us refreshing the page.

It uses Webpack which is a build tool that enables many of the features listed above. It also includes Babel which transpiles our JavaScript from ES6 to be compatible with older browsers. It also includes Autoprefixer for the cross browser CSS compatibility, ESLint for linting, and Jest for testing.

Later in this class we will be giving a class on how to set this up ourselves, but for now `create-react-app` allows us to worry more about our code than configuration!

```bash
$ npm i -g create-react-app
$ create-react-app blog-app
$ cd blog-app
$ atom .
$ npm run start
```

> Here you will begin setting up a blog app that you will continue working on during this lesson's exercises. For demonstration purposes, We will be creating a simple "hello world" app.

After running `$ npm run start`, we can view the app at `http://localhost:3000`

`create-react-app` provides us with all the necessary tools and configuration necessary to start writing React. `npm run start` refers to an included script that starts up the development server.

Along with installing the necessary dependencies, it creates an initial app skeleton that looks like this...

```bash
├──README.md
├──  favicon.ico
├──  index.html
├──  node_modules
├──  package.json
└──  src
    ├──  App.css
    ├──  App.js
    ├──  index.css
    ├──  index.js
    └──  logo.svg
```

Most of the important files, which are primarily the ones where we will be working today, are in the `/src` directory.

---

### Stop / Catch Up / Investigate

Take some time and look at what's been generated. Specifically look in `App.js` and `index.js`

---

### We Do: Hello World - A Very Basic Component (10 minutes)

The basic unit you'll be working with in ReactJS is a **component**.
* It sounds like a simple word, but using "components" is a pretty different way of approaching web development.

* Components can be thought of as functional elements that takes in data and as a result, produce a dynamic UI.

Throughout class we have separated HTML, CSS and Javascript.
* With components, the lines between those three become a bit blurry.
* Instead, we organize our web apps according to small, reusable components that define their own content, presentation and behavior.

What does a component look like? Let's start with a simple "Hello World" example...

To start, in our `/src/App.js` file, let's remove the contents and in its place add this component definition...

```js
// bring in React and Component instance from React
import React, {Component} from 'react'

// define our Hello component
class Hello extends Component {
  // what should the component render
  render () {
    // Make sure to return some UI
    return (
      <h1>Hello World!</h1>
    )
  }
}

export default Hello
```

Let's break down the things we see here...

##### `class Hello`
This is the component we're creating. In this example, we are creating a "Hello" component.

##### `extends Component`
This is the React library class we inherit from to create our component definition.

##### `render()`
Every component has, at minimum, a render method. It generates a **Virtual DOM** node that will be added to the actual DOM.
* Looks just like a regular ol' DOM node, but it's not yet attached to the DOM.

##### `export default Hello`
This exposes the Hello class to other files which import from the App.js file. The `default` keyword means that any import that's name doesn't match a named export will automatically revert to this. Only one default is allowed per file.

#### JSX (5 minutes)

Let's talk about the value that the render method returns. It looks an awful lot like an HTML heading, but it's not. We often write out React components in JSX.

JSX is [a language that compiles to Javascipt](http://blog.yld.io/2015/06/10/getting-started-with-react-and-node-js/#.V8eDk5MrJPN) that allows us to write code that strongly resembles HTML. It is eventually compiled to lightweight JavaScript objects.

Your Hello component's render method:

* Currently returns JSX, not HTML.
The JSX creates a heading with 'Hello World!'.
* Your component reads this and renders a "Hello World!" heading.

> React can be written without JSX. If you want to learn more, [check out this blog post](http://jamesknelson.com/learn-raw-react-no-jsx-flux-es6-webpack/).  

* React then uses these objects to build out a "Virtual DOM" -- more on that in just a bit.


**Virtual DOM? How is that different from the usual DOM?** (10 minutes)

You may have noticed that our `src/index.js` code mentions ReactDOM. ReactDOM doesn't refer to the same DOM we know. Instead, it refers to a Virtual DOM. The Virtual DOM is a key piece of how React works.

The Virtual DOM is a Javascript representation of the actual DOM. The virtual DOM is a staging area for changes that will eventually be implemented.

* Because of that, React can keep track of changes in the actual DOM by comparing different instances of the Virtual DOM.
* React then isolates the changes between old and new instances of the Virtual DOM and then only updates the actual DOM with the necessary changes.
* By only making the "necessary changes," as opposed to re-rendering an entire view altogether, we save up on processing power.
* This is not unlike Git, with which you compare the difference -- or `diff` -- between two commits.

![Virtual DOM Diagram](https://docs.google.com/drawings/d/11ugBTwDkqn6p2n5Fkps1p3Elp8ZToIRzXzvM4LJMYaU/pub?w=543&h=229)

> If you're interested in learning more about the Virtual DOM, [check this video out](https://www.youtube.com/watch?v=-DX3vJiqxm4).

So we've created the template for our component. Now, let's use `/src/index.js` to load in our new component and render it on the DOM...

```js
import React from 'react'
import ReactDOM from 'react-dom'
import Hello from './App.js'

ReactDOM.render(
  <Hello />,
  document.getElementById('root')
)
```
> In place of `ReactDOM.render` some tutorials will use React.renderComponent, which has been phased out. The change is outlined [here](http://bit.ly/1E81Whs).

`ReactDOM.render` takes the Virtual DOM node created by `extends Component` and adds it to the actual DOM. It takes two arguments...

  1. The component.
  2. The DOM element we want to append it to.

#### Review
What is `<Hello />` written in? **JSX.**
* When we say `<Hello />`, in plain Javascript we are actually saying `React.DOM.div( null, "Hello world.")`
  * Basically, a string of React methods that create a virtual DOM node.

> **NOTE:** Whenever you use a self-closing tag in JSX, you **MUST** end it with a `/` like `<Hello />` in the above example.

---

### Hello World: A Little Dynamic (15 minutes)

Our `Hello` component isn't too helpful. Let's make it more interesting.
* Rather than simply display "Hello world", let's display a greeting to the user.
* So the question is, how do we feed a name to our `Hello` component without hardcoding it into our render method?

First, we pass in data wherever we are rendering our component, in this case in `src/index.js`...

```js
import React from 'react'
import ReactDOM from 'react-dom'
import Hello from './App.js'

ReactDOM.render(
  <Hello name={"Nick"} />,
  document.getElementById('root')
)
```

Then in our component definition, we have a reference to that data via as a property on the `props` object...

```js
class Hello extends Component {
  render () {
    return (
      <h1>Hello {this.props.name}</h1>
    )
  }
}
```

In the above example, we replaced "world" with `{this.props.name}`.

#### What are `.props`?

Properties! Every component has `.props`
* Properties are immutable. That is, they cannot be changed while your program is running.
* We define properties in development and pass them in as attributes to the JSX element in our `.render` method.

First we can pass multiple properties to our component when its rendered in `src/index.js`..

```js
import React from 'react';
import ReactDOM from 'react-dom'
import Hello from './App.js'

ReactDOM.render(
  <Hello name={"Nick"} age={24} />,
  document.getElementById('root')
)
```

Then in our component definition we have access to both values...

```js
class Hello extends Component {
  render () {
    return (
      <div>
        <h1>Hello {this.props.name}</h1>
        <p>You are {this.props.age} years old</p>
      </div>
    )
  }
}

```

> **NOTE:** The return statement in `render` can only return one DOM element. You can, however, place multiple elements within a parent DOM element, like we do in the previous example with `<div>`.

---

## Break (10 minutes)

---

### You Do: A Blog Post (25 minutes)

Let's have some practice creating a React component from scratch. How about a blog post?
* Create a `post` object literal in `src/index.js` that has the below properties.
  1. `title`
  2. `author`
  3. `body`
  4. `comments` (array of strings)
* Render these properties using a Post component.
* The HTML (or more accurately, JSX) composition of your Post is up to you.

#### [Solution](https://github.com/ga-wdi-exercises/simple-react-blog/commit/f1088165898d1a20df956647c8e9b5ed67d9ad32)

---

## Closing (5 minutes)
* Why do we use components in React?
* What is the Virtual DOM?
* What is JSX?
* What features does `create-react-app` give us?
