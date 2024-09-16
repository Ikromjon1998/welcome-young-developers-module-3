## **Session 8: React Hooks: Special Powers for Your Website!** 🛠️

In this session, we’ll explore **React hooks**—special functions that let you "hook into" React features without writing a class. We'll focus on hooks like `useEffect` for managing side effects and `useContext` for accessing global state. We'll also apply **Tailwind CSS** to style our examples.

---

### **1. Objective**

By the end of this session, you’ll learn how to:
- Use React hooks like `useEffect` and `useContext`.
- Understand the purpose and use cases of different hooks.
- Implement practical examples to manage side effects and global state.
- Style components using **Tailwind CSS**.

---

### **2. Introduction to Hooks**

Hooks are functions that let you use state and other React features in functional components. They are a way to use state and other React features without writing a class.

#### **2.1 Commonly Used Hooks**

- **`useState`**: Allows you to add state to functional components.
- **`useEffect`**: Manages side effects like data fetching or subscriptions.
- **`useContext`**: Provides a way to share values across components without prop drilling.

---

### **3. Using `useEffect` for Side Effects** 🔄

The `useEffect` hook lets you perform side effects in your components, such as fetching data, updating the DOM, or subscribing to external events.

#### **3.1 Example: Fetching Data with `useEffect`**

Let’s create a component that fetches and displays a list of users when the component mounts.

```javascript
import React, { useState, useEffect } from 'react';

function UserList() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/users');
        const data = await response.json();
        setUsers(data);
      } catch (error) {
        setError('Failed to fetch users.');
      } finally {
        setLoading(false);
      }
    };

    fetchData();
  }, []); // Empty dependency array means this effect runs once when the component mounts

  if (loading) return <div className="text-center text-gray-500">Loading...</div>;
  if (error) return <div className="text-center text-red-500">{error}</div>;

  return (
    <div className="max-w-2xl mx-auto mt-10 p-6 bg-gray-100 rounded shadow-lg">
      <h2 className="text-xl font-bold mb-4">User List</h2>
      <ul className="space-y-2">
        {users.map((user) => (
          <li key={user.id} className="p-4 bg-white rounded shadow">
            <p className="text-lg font-semibold">{user.name}</p>
            <p className="text-gray-600">{user.email}</p>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default UserList;
```

**Explanation**:
- **`useEffect`**: Executes the `fetchData` function once when the component mounts.
- **Loading State**: Displays a loading message while data is being fetched.
- **Error Handling**: Shows an error message if the fetch fails.
- **Tailwind CSS**: Used for styling the user list and loading/error messages.

---

### **4. Using `useContext` for Global State** 🌐

The `useContext` hook allows you to access global state in your components without passing props manually.

#### **4.1 Example: Using `useContext`**

First, create a context to provide and consume global state.

```javascript
import React, { createContext, useContext, useState } from 'react';

// Create a Context
const ThemeContext = createContext();

export function ThemeProvider({ children }) {
  const [theme, setTheme] = useState('light');

  const toggleTheme = () => {
    setTheme((prevTheme) => (prevTheme === 'light' ? 'dark' : 'light'));
  };

  return (
    <ThemeContext.Provider value={{ theme, toggleTheme }}>
      {children}
    </ThemeContext.Provider>
  );
}

// A component that consumes the context
function ThemedComponent() {
  const { theme, toggleTheme } = useContext(ThemeContext);

  return (
    <div className={`p-6 ${theme === 'light' ? 'bg-white text-black' : 'bg-gray-800 text-white'} rounded shadow`}>
      <h2 className="text-xl font-bold">Current Theme: {theme}</h2>
      <button
        onClick={toggleTheme}
        className="mt-4 px-4 py-2 bg-blue-500 text-white rounded hover:bg-blue-600"
      >
        Toggle Theme
      </button>
    </div>
  );
}

export default ThemedComponent;
```

**Explanation**:
- **Context Creation**: `ThemeContext` is created to manage theme state.
- **Context Provider**: `ThemeProvider` provides the theme and a function to toggle it.
- **Context Consumer**: `ThemedComponent` consumes the theme context and provides a button to toggle the theme.
- **Tailwind CSS**: Used for styling based on the theme (light or dark).

---

### **5. Tailwind CSS for Styling** 🎨

We use **Tailwind CSS** to style our components:
- **Conditional Styling**: Apply different styles based on the theme or state.
- **Utility Classes**: Use Tailwind classes like `bg-gray-100`, `p-6`, and `rounded` to style components.

#### **5.1 Tailwind CSS Installation (Recap)**

If you need to install or configure **Tailwind CSS**, refer back to [Session 6](#) for the installation guide.

---

### **6. Recap and What’s Next** 🔄

In this session, we learned how to:
- Use **React hooks** like `useEffect` for managing side effects and `useContext` for global state.
- Implement practical examples with data fetching and context management.
- Style components with **Tailwind CSS**.
