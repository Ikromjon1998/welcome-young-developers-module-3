## **Session 9: React Router: Navigating Your App Like a Pro!** 🚀

In this session, we’ll dive into **React Router**—the library that allows you to build a multi-page experience in a single-page application. We'll learn how to handle routing, create dynamic routes, and work with route parameters. Plus, we’ll use **Tailwind CSS** to style our navigation components.

---

### **1. Objective**

By the end of this session, you’ll learn how to:
- Implement **React Router** for client-side routing.
- Define routes and handle navigation within a React app.
- Create dynamic routes and pass parameters.
- Style navigation and active links using **Tailwind CSS**.

---

### **2. Introduction to React Router**

**React Router** is a standard library for routing in React. It enables you to build single-page applications (SPAs) with navigation across different views while keeping the experience seamless and fast.

#### **2.1 Key Features of React Router**

- **`<BrowserRouter>`**: Wraps your app and enables routing.
- **`<Route>`**: Defines a path and the component to render.
- **`<Link>`**: Enables navigation between routes without reloading the page.
- **Dynamic Routing**: Allows the use of parameters in the route path.

---

### **3. Setting Up Routes with React Router** 🛤️

To start, you need to install and configure **React Router** in your app.

```bash
npm install react-router-dom
```

#### **3.1 Example: Basic Routing Setup**

Let’s create a simple navigation system with three routes: Home, About, and Contact.

```javascript
import React from 'react';
import { BrowserRouter as Router, Route, Routes, Link } from 'react-router-dom';

function Home() {
  return <h2 className="text-2xl font-bold">Home Page</h2>;
}

function About() {
  return <h2 className="text-2xl font-bold">About Page</h2>;
}

function Contact() {
  return <h2 className="text-2xl font-bold">Contact Page</h2>;
}

function App() {
  return (
    <Router>
      <nav className="p-6 bg-gray-800 text-white">
        <ul className="flex space-x-4">
          <li><Link to="/" className="hover:underline">Home</Link></li>
          <li><Link to="/about" className="hover:underline">About</Link></li>
          <li><Link to="/contact" className="hover:underline">Contact</Link></li>
        </ul>
      </nav>

      <div className="p-6">
        <Routes>
          <Route path="/" element={<Home />} />
          <Route path="/about" element={<About />} />
          <Route path="/contact" element={<Contact />} />
        </Routes>
      </div>
    </Router>
  );
}

export default App;
```

**Explanation**:
- **`<Router>`**: Wraps your app and provides routing functionality.
- **`<Link>`**: Navigates between pages without reloading.
- **`<Routes>` and `<Route>`**: Defines the routes and which component to display for each path.
- **Tailwind CSS**: Used for styling the navigation bar and page content.

---

### **4. Dynamic Routes and Route Parameters** 🔧

React Router supports dynamic routing, where the path can include parameters. This is useful for detail pages like user profiles or product details.

#### **4.1 Example: Dynamic Routing with Parameters**

Let’s create a dynamic route for displaying user profiles based on their ID.

```javascript
import React from 'react';
import { BrowserRouter as Router, Routes, Route, Link, useParams } from 'react-router-dom';

function UserProfile() {
  const { id } = useParams(); // Get the route parameter
  return <h2 className="text-2xl font-bold">User Profile for User ID: {id}</h2>;
}

function App() {
  return (
    <Router>
      <nav className="p-6 bg-gray-800 text-white">
        <ul className="flex space-x-4">
          <li><Link to="/user/1" className="hover:underline">User 1</Link></li>
          <li><Link to="/user/2" className="hover:underline">User 2</Link></li>
        </ul>
      </nav>

      <div className="p-6">
        <Routes>
          <Route path="/user/:id" element={<UserProfile />} />
        </Routes>
      </div>
    </Router>
  );
}

export default App;
```

**Explanation**:
- **`useParams`**: Extracts route parameters like `id` from the URL.
- **Dynamic Route**: `/user/:id` allows for dynamic rendering of user profiles based on the `id`.
- **Tailwind CSS**: Used to style the navigation and profile display.

---

### **5. Tailwind CSS for Navigation Styling** 🎨

We’ll use **Tailwind CSS** to create a responsive and visually appealing navigation menu.

#### **5.1 Tailwind Classes for Navigation**

- **Responsive Design**: Use Tailwind’s utility classes like `p-6`, `bg-gray-800`, and `hover:underline` for styling.
- **Active Link Styling**: Tailwind can conditionally apply styles to highlight active links.

For example, you can apply conditional styling for active routes with `NavLink`:

```javascript
import { NavLink } from 'react-router-dom';

function Navigation() {
  return (
    <nav className="p-6 bg-gray-800 text-white">
      <ul className="flex space-x-4">
        <li>
          <NavLink
            to="/"
            className={({ isActive }) => (isActive ? "text-yellow-400" : "hover:underline")}
          >
            Home
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/about"
            className={({ isActive }) => (isActive ? "text-yellow-400" : "hover:underline")}
          >
            About
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/contact"
            className={({ isActive }) => (isActive ? "text-yellow-400" : "hover:underline")}
          >
            Contact
          </NavLink>
        </li>
      </ul>
    </nav>
  );
}
```

---

### **6. Recap and What’s Next** 🔄

In this session, we covered:
- Setting up routing with **React Router** for multi-page navigation.
- Using **dynamic routes** and handling **route parameters**.
- Styling navigation menus using **Tailwind CSS**.

Next, we’ll explore advanced routing techniques, such as nested routes and redirection, in the upcoming session!

---

This structure keeps the format consistent with Session 8 while introducing **React Router** and dynamic routing.
