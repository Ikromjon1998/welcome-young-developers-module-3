### **Session 3: React Props: Pass the Baton!** 🏅

In Session 3, we'll dive deep into **React Props**, a crucial concept that allows components to communicate with each other. By the end of this session, you'll understand how to pass data from one component to another, making your React applications more dynamic and interactive.

---

### **1. Recap of Session 2**

Before we start, let's quickly recap what we covered in Session 2:
- We learned about **React components**, both functional and class components.
- We explored **JSX**, how it allows us to embed JavaScript in our HTML-like code.
- We created and rendered components and nested them within each other.

Now, we're ready to learn about **props** (short for properties), which will let us pass data between components.

### **2. What are Props?** 🤔

**Props** are like the parameters of a function. They allow you to pass data from a parent component to a child component, making it possible to reuse components with different data. 

Think of props as a way to "customize" a component by passing information to it. This is what makes React components flexible and reusable.

#### **2.1 How Props Work: An Analogy**

Imagine you’re a chef in a restaurant. You have a recipe (the component), but you need ingredients (props) to prepare the dish. The customer (parent component) tells you what ingredients to use, and you (the child component) make the dish accordingly.

In React, the parent component passes the props to the child component, which uses those props to render content.

### **3. Passing Props to Components** 📦

Let's see how props work with an example. We’ll start by creating a parent component that passes props to a child component.

#### **3.1 Creating a Simple Parent-Child Component Structure**

First, let's create a child component called `Greeting.js` that accepts a prop and displays it:

```javascript
import React from 'react';

function Greeting(props) {
  return <h2>Hello, {props.name}!</h2>;
}

export default Greeting;
```

In this example, the `Greeting` component takes a prop called `name` and displays it inside an `<h2>` element.

Now, let’s create a parent component called `App.js` that passes a name to the `Greeting` component:

```javascript
import React from 'react';
import Greeting from './Greeting';

function App() {
  return (
    <div className="App">
      <Greeting name="Alice" />
      <Greeting name="Bob" />
      <Greeting name="Charlie" />
    </div>
  );
}

export default App;
```

Here’s what’s happening:
- The `App` component renders three `Greeting` components.
- Each `Greeting` component receives a different `name` prop (`"Alice"`, `"Bob"`, and `"Charlie"`).

When you run this app, it will display:

```html
Hello, Alice!
Hello, Bob!
Hello, Charlie!
```

This is how props allow you to reuse components with different data.

### **4. Props in Action: Building a Profile Card** 🖼️

Let’s build a more practical example by creating a `ProfileCard` component that takes several props to display a user’s profile.

#### **4.1 Creating the `ProfileCard` Component**

Here’s what the `ProfileCard` component might look like:

```javascript
import React from 'react';

function ProfileCard(props) {
  return (
    <div className="profile-card">
      <img src={props.imageUrl} alt="Profile" />
      <h2>{props.name}</h2>
      <p>Age: {props.age}</p>
      <p>Bio: {props.bio}</p>
    </div>
  );
}

export default ProfileCard;
```

This component uses four props:
- `imageUrl` for the profile picture.
- `name` for the user’s name.
- `age` for the user’s age.
- `bio` for a short bio of the user.

#### **4.2 Passing Props from the Parent Component**

Now, let's use the `ProfileCard` component in `App.js` and pass it some props:

```javascript
import React from 'react';
import ProfileCard from './ProfileCard';

function App() {
  return (
    <div className="App">
      <ProfileCard 
        imageUrl="https://example.com/profile.jpg"
        name="John Doe"
        age={30}
        bio="A passionate developer and lifelong learner."
      />
      <ProfileCard 
        imageUrl="https://example.com/profile2.jpg"
        name="Jane Smith"
        age={28}
        bio="A creative designer who loves to explore new ideas."
      />
    </div>
  );
}

export default App;
```

Here’s what’s happening:
- The `App` component renders two `ProfileCard` components.
- Each `ProfileCard` receives different props, which are displayed in the UI.

When you run the app, it will show two profile cards, each with a different image, name, age, and bio.

### **5. Interactive Exercise: Build Your Own Prop-Driven Component** 🎯

It’s time to practice! Let’s build a component that displays information about your favorite book.

#### **Exercise Steps:**
1. **Create a new component** called `BookCard.js` that takes props like `title`, `author`, `coverImage`, and `description`.
2. **Use the `BookCard` component** inside `App.js` and pass the required props.
3. **Render multiple `BookCard` components** to display information about different books.

Here’s a hint to get you started:

```javascript
import React from 'react';

function BookCard(props) {
  return (
    <div className="book-card">
      <img src={props.coverImage} alt="Book Cover" />
      <h2>{props.title}</h2>
      <p>Author: {props.author}</p>
      <p>{props.description}</p>
    </div>
  );
}

export default BookCard;
```

Don’t forget to style your `BookCard` component to make it look nice!

### **6. Understanding Default Props** 🛠️

Sometimes, you might want to provide a **default value** for a prop in case it’s not passed by the parent component. React allows you to do this easily.

#### **6.1 Setting Default Props**

Here’s how you can set default props in your `BookCard` component:

```javascript
import React from 'react';

function BookCard(props) {
  return (
    <div className="book-card">
      <img src={props.coverImage} alt="Book Cover" />
      <h2>{props.title}</h2>
      <p>Author: {props.author}</p>
      <p>{props.description}</p>
    </div>
  );
}

// Setting default props
BookCard.defaultProps = {
  coverImage: 'https://example.com/default-cover.jpg',
  title: 'Unknown Title',
  author: 'Unknown Author',
  description: 'No description available.'
};

export default BookCard;
```

If the parent component doesn’t pass one of these props, the default value will be used instead.

### **7. Prop Types: Ensuring Correct Props** ✅

React also allows you to **validate the props** being passed to a component using a package called `prop-types`. This ensures that the component receives the correct type of props.

#### **7.1 Installing and Using Prop Types**

First, you need to install the `prop-types` package:

```bash
npm install prop-types
```

Then, you can use it in your `BookCard` component:

```javascript
import React from 'react';
import PropTypes from 'prop-types';

function BookCard(props) {
  return (
    <div className="book-card">
      <img src={props.coverImage} alt="Book Cover" />
      <h2>{props.title}</h2>
      <p>Author: {props.author}</p>
      <p>{props.description}</p>
    </div>
  );
}

// Setting default props
BookCard.defaultProps = {
  coverImage: 'https://example.com/default-cover.jpg',
  title: 'Unknown Title',
  author: 'Unknown Author',
  description: 'No description available.'
};

// Defining prop types
BookCard.propTypes = {
  coverImage: PropTypes.string,
  title: PropTypes.string.isRequired,
  author: PropTypes.string.isRequired,
  description: PropTypes.string
};

export default BookCard;
```

Here’s what this does:
- `PropTypes.string`: Ensures that the prop is a string.
- `isRequired`: Makes sure the prop is passed; otherwise, React will show a warning.

This is a good practice to avoid bugs and ensure your components are used correctly.

### **8. Recap and What's Next**

In this session, you’ve learned:
- What props are and how they allow data to be passed between components.
- How to create and use components that accept props.
- How to set default props and validate them using prop types.

Next time, we’ll explore **state** in React, which allows components to manage their own data and react to user inputs, making our applications even more dynamic!

### **9. Additional Resources**

- [React Props Documentation](https://reactjs.org/docs/components-and-props.html) - Learn more about using props in React.
- [Prop Types Documentation](https://reactjs.org/docs/typechecking-with-proptypes.html) - Understand how to validate props with prop types.
- [React Default Props](https://reactjs.org/docs/react-component.html#defaultprops) - Official documentation on setting default props.

