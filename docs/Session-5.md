## **Session 5: Project 6: Build a To-Do List!** ✅

In this session, we will apply what we've learned about **props** and **state** to build a fully interactive **To-Do List**. By the end of this session, you’ll have a functional app where users can add, track, and manage their tasks. Let’s break it down step-by-step!

---

### **1. Recap of Key Concepts**

Before we jump into the project, let’s quickly review some important concepts that you’ll use:
- **Props**: Allow data to be passed from one component to another.
- **State**: Allows components to hold and manage data that can change over time (e.g., task completion status).
- **Event Handling**: Enables user interaction (e.g., clicking a button to add a new task).

With these concepts in mind, we’re ready to build our **To-Do List** app!

### **2. Breaking Down the To-Do List into Components** 🛠️

We’ll start by planning the structure of our app. A typical To-Do List app can be broken down into several components:
1. **App Component**: The main component that holds everything together.
2. **ToDoInput Component**: A form for users to add new tasks.
3. **ToDoList Component**: Displays a list of tasks.
4. **ToDoItem Component**: Represents each individual task in the list.

#### **2.1 The Component Hierarchy**

```plaintext
App
│
├── ToDoInput
│
└── ToDoList
     └── ToDoItem (for each task)
```

This structure will help us keep the code clean and modular.

### **3. Managing To-Do Items with State** 📋

The core of our app’s functionality will revolve around **state**. The **App Component** will manage the state that stores all the tasks.

#### **3.1 Setting Up State in the `App` Component**

Let’s start by setting up the state that will hold our list of to-dos.

```javascript
import React, { useState } from 'react';
import ToDoInput from './ToDoInput';
import ToDoList from './ToDoList';

function App() {
  const [todos, setTodos] = useState([]);

  return (
    <div className="App">
      <h1>To-Do List</h1>
      <ToDoInput setTodos={setTodos} todos={todos} />
      <ToDoList todos={todos} setTodos={setTodos} />
    </div>
  );
}

export default App;
```

Here’s what we’re doing:
- **State**: We use `useState` to create a `todos` state that holds the list of tasks.
- **Props**: The `setTodos` function and the `todos` state are passed down as props to the child components so they can manage the tasks.

### **4. Adding New Tasks** 📝

We’ll use the **ToDoInput Component** to allow users to add new tasks. This component will have an input field and a button to submit the task.

#### **4.1 Creating the `ToDoInput` Component**

```javascript
import React, { useState } from 'react';

function ToDoInput({ setTodos, todos }) {
  const [input, setInput] = useState('');

  const addTodo = () => {
    const newTodo = {
      id: Math.random(),
      text: input,
      completed: false
    };
    setTodos([...todos, newTodo]);
    setInput(''); // Clear the input after adding the task
  };

  return (
    <div>
      <input 
        type="text" 
        value={input} 
        onChange={(e) => setInput(e.target.value)} 
        placeholder="Add a new task"
      />
      <button onClick={addTodo}>Add Task</button>
    </div>
  );
}

export default ToDoInput;
```

Here’s what’s happening:
- **State**: We use `useState` to manage the `input` field.
- **Adding a Task**: When the "Add Task" button is clicked, the `addTodo` function creates a new task and adds it to the list of tasks stored in `todos`.

### **5. Displaying the To-Do List** 📜

Now, we’ll use the **ToDoList Component** to display the list of tasks. Each task will be rendered using the **ToDoItem Component**.

#### **5.1 Creating the `ToDoList` Component**

```javascript
import React from 'react';
import ToDoItem from './ToDoItem';

function ToDoList({ todos, setTodos }) {
  return (
    <ul>
      {todos.map((todo) => (
        <ToDoItem key={todo.id} todo={todo} setTodos={setTodos} todos={todos} />
      ))}
    </ul>
  );
}

export default ToDoList;
```

This component:
- Maps over the `todos` array and renders a `ToDoItem` for each task.
- Passes down each `todo` as a prop to the `ToDoItem` component.

### **6. Marking Tasks as Completed** ✅

Next, we’ll implement the functionality to mark a task as completed by clicking on it. When a task is clicked, its `completed` status should toggle.

#### **6.1 Creating the `ToDoItem` Component**

```javascript
import React from 'react';

function ToDoItem({ todo, setTodos, todos }) {
  const toggleComplete = () => {
    const updatedTodos = todos.map((t) =>
      t.id === todo.id ? { ...t, completed: !t.completed } : t
    );
    setTodos(updatedTodos);
  };

  return (
    <li 
      onClick={toggleComplete} 
      style={{ textDecoration: todo.completed ? 'line-through' : 'none' }}
    >
      {todo.text}
    </li>
  );
}

export default ToDoItem;
```

Here’s how it works:
- **Toggle Completion**: When the user clicks a task, the `toggleComplete` function is triggered, which toggles the `completed` property of the clicked task.
- **Styling**: The task is styled with a line-through if it’s marked as completed.

### **7. Recap and What's Next**

In this session, we built a fully functional **To-Do List** using **props** and **state**:
- We broke the project down into smaller components like `App`, `ToDoInput`, `ToDoList`, and `ToDoItem`.
- We used **state** to manage the list of tasks and their completion status.
- We used **props** to pass down functions and data between parent and child components.

In the next session, we’ll learn about **lifting state up** and managing more complex interactions between components.

### **8. Interactive Challenge: Add Features to Your To-Do List** 🎯

Here are a few challenges to extend your To-Do List app:
1. **Add a "Delete Task" Button**: Allow users to delete tasks from the list.
2. **Filter Tasks**: Create buttons to filter tasks by "All", "Completed", and "Incomplete".
3. **Edit Tasks**: Add functionality to edit a task after it’s added.

### **9. Additional Resources**

- [React State and Lifecycle](https://reactjs.org/docs/state-and-lifecycle.html) - Learn more about managing state in React.
- [Props in React](https://reactjs.org/docs/components-and-props.html) - Explore how to pass data between components using props.
- [React Developer Tools](https://reactjs.org/docs/react-developer-tools.html) - Use this browser extension to debug your React components.
