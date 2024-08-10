

### **Module 3: Level Up with React: Building Interactive Websites**

### **Session 1: React: A New Way to Build!**

---

**Age Group:** 11-15 years old  
**Session Length:** 1 hour  
**Main Goal:** Introduce students to React, help them set up their development environment, and create a simple React component.

---

### **1. Introduction to the Session (5 minutes)**

**Welcome and Warm-Up:**
- **Icebreaker Question:** Start with a simple question to spark interest: "Who has ever wanted to build their own website? What would it be about?" Let the students share their ideas.
- **Objective Overview:** "Today, we’re going to start learning about a tool called React. It’s going to help us build cool websites that you can interact with, like games or your favorite apps."

### **2. What is React? (10 minutes)**

**Simple Explanation:**
- **Story:** 
  - "Imagine you’re building a LEGO castle. Each piece of LEGO is like a little part of your website. React is like a special set of LEGO blocks that you can use to build really awesome castles—websites that can change and do things when you click on them."
  
**Why React is Special:**
- **Interactive Example:**
  - Open two websites—one static and one interactive (like Facebook or a game website). Show the difference between clicking on a static site (where nothing happens) and an interactive one (where things move or change).
  - "React helps us make websites where things happen when you click, type, or even just move your mouse. It makes the website feel alive!"

**Real-World Connection:**
- **Examples:** 
  - Mention a few popular websites kids might know, like Facebook, Instagram, or YouTube. "Did you know these sites use React to make sure everything works smoothly and quickly? That’s why they’re so fun to use!"

### **3. Setting Up Your React Environment (15 minutes)**

**Step-by-Step Installation:**
- **Tools Required:** 
  - Explain that they’ll need a few tools to get started:
    1. **Node.js**: This is like a magic toolbox that helps you build things with React.
    2. **A Code Editor**: You can use any code editor, but today we’ll use **Visual Studio Code (VS Code)** because it’s easy and fun to use.

**Installation Process:**
- **Guide Students to Install Node.js:**
  1. **Visit the Node.js Website:** "Go to nodejs.org. You’ll see a big green button that says ‘LTS’. Click on that to download."
  2. **Install Node.js:** "Once it’s downloaded, open the file and click ‘Next’ a few times. It’s like installing a game—you just need to keep clicking ‘Next’ until it’s done!"
  3. **Check the Installation:** "After it’s installed, let’s make sure it worked. Open the terminal (or command prompt) and type `node -v` and press enter. You should see a version number. If you see that, you’re ready to go!"

- **Guide Students to Install VS Code:**
  1. **Visit the VS Code Website:** "Go to code.visualstudio.com and click on the download button. Just like Node.js, follow the steps to install it."
  2. **Open VS Code:** "After it’s installed, open it up. You’ll see a blank screen—that’s where we’ll write our code!"

**Setting Up a New React Project:**
- **Creating Your First React App:**
  1. **Open Terminal in VS Code:** "In VS Code, go to ‘View’ and click on ‘Terminal’. This is where we’ll type some commands."
  2. **Create a New React App:** "Type `npx create-react-app my-first-react-app` and press enter. This might take a minute, but what it’s doing is setting up everything we need to start building with React."
  3. **Open the Project:** "Once it’s done, you’ll see a new folder in VS Code called `my-first-react-app`. Click on it to see all the files inside."

- **Start the React App:**
  1. **Run the App:** "Now, let’s see what we’ve created! Type `cd my-first-react-app` to go into the project folder, and then type `npm start`. This will start up our new React app!"
  2. **View the App:** "Your browser should open automatically, showing a spinning React logo. This is our React app running for the first time!"

**Discussion:**
- **Reflect:** "How cool is that? With just a few commands, we’ve created a brand new website! Over the next few sessions, we’ll learn how to change this site to make it our own."

### **4. Exploring React: Your First Component (20 minutes)**

**What are Components?**
- **Explanation:**
  - "In React, a component is like a small part of your website. Think of it like a LEGO piece. You can build a website by putting lots of these components together."

**Creating a Simple Component:**
- **Hands-On Activity:**
  1. **Open the `App.js` File:** "In your project folder, find the file called `App.js` and click on it. This is where we’ll write our first React component."
  2. **Modify the Component:** "You’ll see some code that looks like HTML but a little different. Let’s change the text to say ‘Hello, World!’ instead of the default text."
    ```javascript
    function App() {
      return (
        <div className="App">
          <h1>Hello, World!</h1>
        </div>
      );
    }
    export default App;
    ```
  3. **Save and View:** "After you’ve made the change, save the file (Ctrl + S or Command + S), and go back to your browser. You should see your new text on the screen!"

**Personalizing the Component:**
- **Customize Your Greeting:**
  - "Now, let’s make it more personal! Change the text to say ‘Hello, [Your Name]!’." 
  - Example:
    ```javascript
    function App() {
      return (
        <div className="App">
          <h1>Hello, Alex!</h1>
        </div>
      );
    }
    ```
  - "Replace ‘Alex’ with your name and see how it looks!"

**Challenge:**
- **Add More Elements:**
  - "Let’s make it even cooler! Try adding another element, like a paragraph of text or an emoji."
  - Example:
    ```javascript
    function App() {
      return (
        <div className="App">
          <h1>Hello, Alex!</h1>
          <p>Welcome to my first React app! 🚀</p>
        </div>
      );
    }
    ```

### **5. Interactive Components: Adding a Button (15 minutes)**

**Introduction to Interactive Elements:**
- **Explain:**
  - "Now that we’ve learned how to create a basic component, let’s make it interactive! We’re going to add a button that does something when you click it."

**Building a Button Component:**
- **Hands-On Activity:**
  1. **Add a Button:** "Let’s add a button to our app. Here’s how you can do it:"
    ```javascript
    function App() {
      function handleClick() {
        alert('Button Clicked!');
      }
      return (
        <div className="App">
          <h1>Hello, Alex!</h1>
          <button onClick={handleClick}>Click Me!</button>
        </div>
      );
    }
    ```
  2. **Test the Button:** "Save your file and check your browser. Click the button and see what happens!"

**Discussion:**
- **How it Works:**
  - "The button is listening for clicks, and when you click it, it runs the `handleClick` function, which shows an alert box. This is just a simple example, but you can imagine all the cool things you can do with buttons in React!"

**Interactive Challenge:**
- **Experiment with Buttons:**
  - "Try changing the message in the alert, or add more buttons with different messages. What happens when you click each one?"

### **6. Wrap-Up and Q&A (5 minutes)**

**Recap:**
- **Summary of What We Learned:**
  - "Today, we learned what React is, why it’s special, and how to set up our first React app. We even created our first components and made them interactive with a button!"
  
**Q&A:**
- **Open Floor:** 
  - "Do you have any questions about what we did today? What was your favorite part?"

**Preview of Next Session:**
- **Teaser:**
  - "Next time, we’ll dive deeper into React and start building more complex parts of our website, like different components that can talk to each other. It’s going to be a lot of fun!"

---

**Homework/Extra Practice (Optional):**
- **Explore More:**
 

 - "If you want to practice more, try creating a new component that displays a list of your favorite things, like games, movies, or hobbies. Use what we learned today to make it interactive!"

