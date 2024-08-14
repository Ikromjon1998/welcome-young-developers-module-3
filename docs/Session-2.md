## **Session 2: React Basics: Meet Components and JSX!** 🧩

### **1. Recap of Session 1**

Before we dive into new material, let's quickly recap what we learned in the last session:
- We set up our React development environment.
- We learned about the structure of a React project.
- We created and rendered our first React component.
- We got introduced to JSX, a special syntax that looks like HTML but works in JavaScript.

Now, let's take these concepts further!

### **2. Deep Dive into Components**

Components are the heart and soul of React. They are reusable pieces of code that represent parts of your website. Let’s explore how to create different types of components and understand why they are so powerful.

#### **2.1 Functional Components**

The simplest way to create a component in React is by using a **functional component**. We briefly touched on this in the last session, but now let's look at it in more detail.

A functional component is a JavaScript function that returns JSX. Here's an example:

```javascript
function WelcomeMessage() {
  return (
    <div>
      <h2>Welcome to Your React Journey!</h2>
      <p>This is a functional component.</p>
    </div>
  );
}

export default WelcomeMessage;
```

When you use this component in your app, it will display a heading and a paragraph. The power of functional components lies in their simplicity and reusability.

#### **2.2 Class Components (Optional for Advanced Students)**

While functional components are most common in modern React, you might also encounter **class components**. A class component is another way to create components using ES6 class syntax.

Here’s what a simple class component looks like:

```javascript
import React, { Component } from 'react';

class Greeting extends Component {
  render() {
    return (
      <div>
        <h2>Hello from a Class Component!</h2>
        <p>This is a more advanced concept but still easy to grasp.</p>
      </div>
    );
  }
}

export default Greeting;
```

**Class components** were widely used in older versions of React, but today, functional components with hooks (which we’ll cover in future sessions) are the standard. However, it’s good to know both!

### **3. Understanding JSX in Detail**

JSX is a game-changer in React because it allows you to write what looks like HTML directly inside your JavaScript code. However, it's more than just HTML – it's a powerful way to describe the UI of your React components.

#### **3.1 What Exactly is JSX?**

JSX stands for **JavaScript XML**. It’s a syntax extension that allows you to write HTML-like code in your JavaScript files. But remember, JSX is not HTML – it's JavaScript under the hood.

Here’s an example of JSX:

```jsx
const greeting = <h1>Hello, world!</h1>;
```

This is compiled into JavaScript code that looks like this:

```javascript
const greeting = React.createElement('h1', null, 'Hello, world!');
```

So, JSX makes it easier and more intuitive to create React elements.

#### **3.2 Embedding JavaScript in JSX**

One of the coolest things about JSX is that you can embed JavaScript expressions directly in it using curly braces `{}`.

Here’s an example:

```jsx
const name = 'Alice';
const element = <h1>Hello, {name}!</h1>;
```

In this example, the value of the `name` variable is inserted directly into the JSX. When rendered, the output will be:

```html
<h1>Hello, Alice!</h1>
```

You can also embed any valid JavaScript expression inside the curly braces, like calling a function or performing calculations.

```jsx
const user = {
  firstName: 'Alice',
  lastName: 'Johnson'
};

function formatName(user) {
  return user.firstName + ' ' + user.lastName;
}

const element = <h1>Hello, {formatName(user)}!</h1>;
```

This flexibility makes JSX a powerful tool for creating dynamic and interactive UIs.

### **4. Creating and Rendering Components with JSX**

Let’s take what we’ve learned about components and JSX and put it into practice by building a small React app.

#### **4.1 Building a Simple Component**

We'll start by creating a component called `UserCard`. This component will display a user’s name, age, and a short description.

Here’s how you can create the `UserCard` component:

```javascript
import React from 'react';

function UserCard() {
  const name = 'John Doe';
  const age = 25;
  const description = 'A passionate React learner.';

  return (
    <div className="user-card">
      <h2>{name}</h2>
      <p>Age: {age}</p>
      <p>{description}</p>
    </div>
  );
}

export default UserCard;
```

This component uses JSX to return a block of HTML-like code that includes JavaScript variables.

#### **4.2 Rendering the Component**

To see our `UserCard` component in action, we need to render it in the main `App.js` file.

```javascript
import React from 'react';
import UserCard from './UserCard';

function App() {
  return (
    <div className="App">
      <h1>Meet Our User</h1>
      <UserCard />
    </div>
  );
}

export default App;
```

When you run your React app (`npm start`), you should see the `UserCard` displayed with the user’s name, age, and description.

### **5. Nesting Components**

One of the most powerful features of React is the ability to **nest components**. This means you can create a component and use it inside another component, like building with LEGO blocks.

Let’s create another component called `HobbyList` and nest it inside `UserCard`.

#### **5.1 Creating the `HobbyList` Component**

Here’s the `HobbyList` component:

```javascript
import React from 'react';

function HobbyList() {
  const hobbies = ['Reading', 'Coding', 'Hiking'];

  return (
    <div>
      <h3>Hobbies:</h3>
      <ul>
        {hobbies.map(hobby => (
          <li key={hobby}>{hobby}</li>
        ))}
      </ul>
    </div>
  );
}

export default HobbyList;
```

This component creates a list of hobbies using the `map` function to loop through the `hobbies` array.

#### **5.2 Nesting `HobbyList` in `UserCard`**

Now, let’s nest `HobbyList` inside `UserCard`:

```javascript
import React from 'react';
import HobbyList from './HobbyList';

function UserCard() {
  const name = 'John Doe';
  const age = 25;
  const description = 'A passionate React learner.';

  return (
    <div className="user-card">
      <h2>{name}</h2>
      <p>Age: {age}</p>
      <p>{description}</p>
      <HobbyList />
    </div>
  );
}

export default UserCard;
```

With this change, when you run your app, the user’s hobbies will now be displayed as part of the `UserCard` component.

### **6. Interactive Exercise: Customize Your Components**

Now it's your turn! Here’s a fun exercise to practice what you've learned:

1. **Create a new component** called `ProfilePicture.js` that displays a user’s profile picture.
2. **Nest this component** inside the `UserCard` component, just like we did with `HobbyList`.
3. **Update the `UserCard` component** to pass the picture URL as a prop to `ProfilePicture`.

Here’s a hint to get you started with `ProfilePicture`:

```javascript
import React from 'react';

function ProfilePicture(props) {
  return <img src={props.url} alt="User Profile" />;
}

export default ProfilePicture;
```

Don’t forget to import and use the `ProfilePicture` component inside `UserCard`!

### **7. Recap and What's Next**

In this session, you’ve learned:
- What functional and class components are in React.
- How to use JSX to create elements and embed JavaScript within your components.
- How to build, render, and nest components to create complex UIs.

Next time, we’ll explore **props** in detail, learning how to pass data from one component to another. This will allow us to create even more dynamic and flexible components!

### **8. Additional Resources**

- [React Components Documentation](https://reactjs.org/docs/components-and-props.html) - Learn more about React components and props.
- [MDN Web Docs: Arrow Functions](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions) - A guide to understanding arrow functions in JavaScript, which are commonly used in React.
- [Introduction to JSX](https://reactjs.org/docs/introducing-jsx.html) - Deep dive into JSX with examples.
