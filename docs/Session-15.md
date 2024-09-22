## **Session 15: Project 9: Mini Social Network!** 🌍

In this session, we’ll build a **mini social network** using React. Users will be able to see a list of posts, view individual posts, and read comments. We will use **JSONPlaceholder** to simulate the backend with mock data for posts, users, and comments.

---

### **1. Objective**

By the end of this session, you will:
- Build a React app that mimics a social network with posts, comments, and user profiles.
- Understand how to manage component state and pass data through props.
- Use **React Router** to navigate between different pages (e.g., post list, individual post details).
- Integrate **JSONPlaceholder** API to fetch and display mock data.

---

### **2. Structuring the App: Posts, Comments, and Users** 📝

#### **2.1 App Overview**:
- **Home Page**: Displays a list of posts.
- **Post Page**: Shows details of a selected post and its comments.
- **User Profile**: Displays the profile of the author of a post.

#### **2.2 Key Components**:
1. **`PostList`**: Fetches and displays a list of posts.
2. **`PostDetails`**: Displays the details of a single post and its comments.
3. **`UserProfile`**: Displays the profile of the user who authored the post.

---

### **3. State and Props: Managing Interactions Between Components** 🔄

We’ll use **state** to handle data and **props** to pass data between components. Here’s how data flows between the components:

1. **`PostList`**: Fetches and stores the list of posts.
2. **`PostDetails`**: Receives the post ID via **React Router** and fetches the post’s details and comments.
3. **`UserProfile`**: Receives the user ID from `PostDetails` and fetches the user’s profile data.

---

### **4. Integrating JSONPlaceholder API** 🌐

We’ll use the **JSONPlaceholder** API to fetch posts, comments, and user profiles.

- **Posts Endpoint**: `https://jsonplaceholder.typicode.com/posts`
- **Users Endpoint**: `https://jsonplaceholder.typicode.com/users`
- **Comments Endpoint**: `https://jsonplaceholder.typicode.com/comments`

---

### **5. Building the Components** 🛠️

#### **5.1 `PostList` Component**

This component fetches and displays all posts. Each post has a link to view more details.

```javascript
import React, { useState, useEffect } from 'react';
import { Link } from 'react-router-dom';

function PostList() {
  const [posts, setPosts] = useState([]);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    const fetchPosts = async () => {
      const response = await fetch('https://jsonplaceholder.typicode.com/posts');
      const data = await response.json();
      setPosts(data);
      setLoading(false);
    };
    fetchPosts();
  }, []);

  if (loading) return <div>Loading...</div>;

  return (
    <div className="container mx-auto p-6">
      <h1 className="text-2xl font-bold mb-4">Posts</h1>
      <ul>
        {posts.map(post => (
          <li key={post.id} className="mb-4">
            <Link to={`/posts/${post.id}`}>
              <h2 className="text-xl font-semibold">{post.title}</h2>
              <p>{post.body.slice(0, 100)}...</p>
            </Link>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default PostList;
```

---

#### **5.2 `PostDetails` Component**

This component displays the full post along with the comments. The post ID is passed through the URL parameters.

```javascript
import React, { useState, useEffect } from 'react';
import { useParams, Link } from 'react-router-dom';

function PostDetails() {
  const { postId } = useParams();
  const [post, setPost] = useState(null);
  const [comments, setComments] = useState([]);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    const fetchPost = async () => {
      const response = await fetch(`https://jsonplaceholder.typicode.com/posts/${postId}`);
      const postData = await response.json();
      setPost(postData);

      const commentsResponse = await fetch(`https://jsonplaceholder.typicode.com/comments?postId=${postId}`);
      const commentsData = await commentsResponse.json();
      setComments(commentsData);

      setLoading(false);
    };
    fetchPost();
  }, [postId]);

  if (loading) return <div>Loading...</div>;

  return (
    <div className="container mx-auto p-6">
      <Link to="/">Back to Posts</Link>
      <h1 className="text-2xl font-bold mb-4">{post.title}</h1>
      <p>{post.body}</p>
      <h3 className="text-xl font-semibold mt-6">Comments:</h3>
      <ul>
        {comments.map(comment => (
          <li key={comment.id} className="mb-2">
            <p><strong>{comment.name}:</strong> {comment.body}</p>
          </li>
        ))}
      </ul>
    </div>
  );
}

export default PostDetails;
```

---

#### **5.3 `UserProfile` Component**

This component fetches and displays the user’s profile information based on the user ID.

```javascript
import React, { useState, useEffect } from 'react';
import { useParams } from 'react-router-dom';

function UserProfile() {
  const { userId } = useParams();
  const [user, setUser] = useState(null);
  const [loading, setLoading] = useState(true);

  useEffect(() => {
    const fetchUser = async () => {
      const response = await fetch(`https://jsonplaceholder.typicode.com/users/${userId}`);
      const data = await response.json();
      setUser(data);
      setLoading(false);
    };
    fetchUser();
  }, [userId]);

  if (loading) return <div>Loading...</div>;

  return (
    <div className="container mx-auto p-6">
      <h1 className="text-2xl font-bold">{user.name}</h1>
      <p>Email: {user.email}</p>
      <p>Phone: {user.phone}</p>
      <p>Website: {user.website}</p>
    </div>
  );
}

export default UserProfile;
```

---

### **6. Setting Up React Router for Navigation** 🚦

To navigate between the **PostList**, **PostDetails**, and **UserProfile** components, we will use **React Router**.

#### **6.1 Install React Router**

```bash
npm install react-router-dom
```

#### **6.2 Set Up Routes**

We’ll define routes for the homepage (post list), post details, and user profile.

```javascript
import React from 'react';
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import PostList from './PostList';
import PostDetails from './PostDetails';
import UserProfile from './UserProfile';

function App() {
  return (
    <Router>
      <Routes>
        <Route path="/" element={<PostList />} />
        <Route path="/posts/:postId" element={<PostDetails />} />
        <Route path="/users/:userId" element={<UserProfile />} />
      </Routes>
    </Router>
  );
}

export default App;
```

---
