## **Session 13: React and APIs: Get Data from the Web!** 🌐

In this session, we’ll explore how to fetch data from external APIs and display it in a React application. You’ll learn how to use both the native **`fetch`** function and **Axios** for API requests. For practice, we’ll build an app that pulls user data from the JSONPlaceholder API.

---

### **1. Objective**

By the end of this session, you will:
- Understand what APIs are and how they work.
- Use the **`fetch`** function and **Axios** to retrieve data from external APIs.
- Build a React app that fetches and displays user data using the **JSONPlaceholder** API.

---

### **2. What Are APIs and How Do They Work?** 🤔

An **API** (Application Programming Interface) allows two software systems to communicate and exchange data. It enables you to access data or functionality from another system (like a web service).

#### **2.1 How APIs Work**:
1. **Request**: Your app sends an HTTP request to an external API endpoint.
2. **Response**: The API processes the request and returns data, usually in JSON format.
3. **Consume the Data**: Your app processes the data and displays it.

#### **2.2 Common HTTP Methods**:
- **GET**: Retrieve data from the API (e.g., fetching users, posts).
- **POST**: Send new data to the API (e.g., creating a new post).
- **PUT/PATCH**: Update existing data.
- **DELETE**: Remove data.

---

### **3. Fetching Data from an API using `fetch`** 🌍

The **`fetch`** function is a built-in JavaScript feature used to make HTTP requests. Let's use it to fetch data from **JSONPlaceholder** and display a list of users.

#### **3.1 Example: Fetch Users Using `fetch`**

Let’s create a React component that fetches user data from the JSONPlaceholder API and displays it in a simple list.

1. **Install dependencies** (Optional for styling):
   ```bash
   npm install tailwindcss
   ```

2. **Create the Users component**:

```javascript
import React, { useState, useEffect } from 'react';

function Users() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await fetch('https://jsonplaceholder.typicode.com/users');
        if (!response.ok) {
          throw new Error('Failed to fetch data');
        }
        const data = await response.json();
        setUsers(data);
      } catch (error) {
        setError(error.message);
      } finally {
        setLoading(false);
      }
    };

    fetchData();
  }, []);

  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error}</div>;

  return (
    <div className="container mx-auto p-6">
      <h1 className="text-2xl font-bold mb-4">User List</h1>
      <ul className="list-disc pl-6">
        {users.map((user) => (
          <li key={user.id} className="mb-2">
            <p className="text-lg font-semibold">{user.name}</p>
            <p className="text-gray-600">{user.email}</p>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default Users;
```

**Explanation**:
- **`useEffect`**: We fetch user data when the component mounts (empty dependency array `[]` ensures it runs only once).
- **Error Handling**: Displays an error message if the fetch fails.
- **Loading State**: Displays a loading message while data is being fetched.
- **Tailwind CSS**: Used for styling the user list.

---

### **4. Fetching Data Using Axios** 🚀

**Axios** is a promise-based HTTP client that simplifies making API requests. Let’s rewrite the same example using Axios instead of `fetch`.

#### **4.1 Install Axios**

First, you need to install Axios:

```bash
npm install axios
```

#### **4.2 Example: Fetch Users Using Axios**

```javascript
import React, { useState, useEffect } from 'react';
import axios from 'axios';

function Users() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState(null);

  useEffect(() => {
    const fetchData = async () => {
      try {
        const response = await axios.get('https://jsonplaceholder.typicode.com/users');
        setUsers(response.data);
      } catch (error) {
        setError('Error fetching data');
      } finally {
        setLoading(false);
      }
    };

    fetchData();
  }, []);

  if (loading) return <div>Loading...</div>;
  if (error) return <div>Error: {error}</div>;

  return (
    <div className="container mx-auto p-6">
      <h1 className="text-2xl font-bold mb-4">User List</h1>
      <ul className="list-disc pl-6">
        {users.map((user) => (
          <li key={user.id} className="mb-2">
            <p className="text-lg font-semibold">{user.name}</p>
            <p className="text-gray-600">{user.email}</p>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default Users;
```

**Explanation**:
- **Axios**: We use Axios to simplify the HTTP request process. Axios automatically parses the JSON response, so we don't need to call `.json()` on the response like we do with `fetch`.

---

### **5. Comparing `fetch` and Axios** 🔄

| Feature              | `fetch`                            | Axios                        |
|----------------------|------------------------------------|------------------------------|
| **Built-in Support**  | Native to JavaScript               | External library             |
| **Response Handling** | Must manually parse JSON responses | Automatically parses JSON    |
| **Error Handling**    | Needs custom handling for HTTP errors | Simplified with built-in support |
| **Request Setup**     | Basic configuration                | More customizable and feature-rich |
