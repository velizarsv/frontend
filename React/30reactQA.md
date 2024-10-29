# Senior React Developer Interview Guide

## Interview Questions and Answers

### Section 1: React Core Concepts

1. **What is React and why was it developed?**
   - **Answer**: React is a JavaScript library for building user interfaces, developed by Facebook to manage UI components efficiently and improve rendering performance using a virtual DOM.

2. **What are React components?**
   - **Answer**: Components are independent, reusable UI elements in React. They can be functional or class-based and contain logic, styles, and even nested components.

3. **Explain the difference between state and props.**
   - **Answer**: Props are read-only attributes passed down from a parent component, while the state is a local data source that controls component behavior and can be updated with `setState` in class components or `useState` in functional components.

4. **What is the virtual DOM and why is it useful?**
   - **Answer**: The virtual DOM is an in-memory representation of the real DOM. React uses it to optimize updates by calculating differences and only re-rendering changed elements, improving performance.

5. **How does the useState hook work?**
   - **Answer**: `useState` initializes a state variable and provides a function to update it. The component re-renders whenever the state changes.

### Section 2: Advanced React and Hooks

6. **Explain the useEffect hook and how it can manage side effects.**
   - **Answer**: `useEffect` allows running side effects in functional components. By default, it runs after every render, but with a dependency array, it can run conditionally based on specific variables.

7. **How do you prevent re-renders in React?**
   - **Answer**: Techniques include memoization with `React.memo`, `useCallback`, and `useMemo` hooks, as well as optimizing component structures and managing dependencies effectively in hooks.

8. **Describe context in React and when to use it.**
   - **Answer**: React Context provides a way to pass data through the component tree without props drilling, suitable for global settings like themes or authentication.

9. **How does React handle event delegation?**
   - **Answer**: React uses a single event listener at the root level for efficiency, delegating events through the virtual DOM instead of attaching individual listeners to each component.

10. **What is the difference between useCallback and useMemo?**
    - **Answer**: `useCallback` memoizes functions, while `useMemo` memoizes values. Both prevent unnecessary recalculations or re-creations of functions and values on re-renders.

### Section 3: Optimization and Performance

11. **How can you optimize component re-renders?**
    - **Answer**: Optimizations include using `React.memo`, `useCallback`, `useMemo`, lazy loading, code splitting, and efficient dependency management in hooks.

12. **What are React lazy loading and Suspense?**
    - **Answer**: `React.lazy` enables code-splitting components, loading them only when needed. `Suspense` allows rendering fallback content while waiting for the component to load.

13. **Explain code splitting and its benefits.**
    - **Answer**: Code splitting divides a large application bundle into smaller chunks, improving load times and performance by loading only necessary parts of the application.

14. **How would you prevent prop drilling?**
    - **Answer**: Prop drilling can be avoided using Context, Redux, or hooks like `useContext` to share data without passing props through multiple layers.

15. **What is server-side rendering (SSR) in React, and when would you use it?**
    - **Answer**: SSR renders React components on the server, delivering a fully populated HTML to clients. It's useful for improving SEO and faster initial page load times.

### Section 4: Styling and State Management

16. **Describe different ways to style React components.**
    - **Answer**: Styles can be added via CSS files, inline styles, CSS Modules, styled-components, or libraries like Emotion for scoped and dynamic styling.

17. **What are CSS Modules, and how do they help in React projects?**
    - **Answer**: CSS Modules localize CSS to specific components, preventing global class conflicts and promoting modularity.

18. **Explain Redux and when to use it in React applications.**
    - **Answer**: Redux is a state management library for predictable state sharing across React components, ideal for large applications with complex data flows.

19. **How would you connect a Redux store to a React component?**
    - **Answer**: Connect the store using `connect` from `react-redux` or by using hooks such as `useSelector` and `useDispatch` to interact with the state and dispatch actions.

20. **What is the purpose of `redux-thunk` middleware?**
    - **Answer**: `redux-thunk` enables asynchronous actions in Redux by allowing action creators to return functions instead of plain action objects.

### Section 5: Testing and Debugging

21. **How do you test React components?**
    - **Answer**: Use tools like Jest for unit tests, React Testing Library for component rendering, and Enzyme for snapshot and behavioral tests.

22. **Explain snapshot testing and its usefulness.**
    - **Answer**: Snapshot testing captures component render outputs. It ensures UI consistency by comparing renders to saved snapshots.

23. **What is the difference between shallow and deep rendering in testing?**
    - **Answer**: Shallow rendering tests a component in isolation without its children, while deep rendering tests a component and its child components together.

24. **How can you debug React components?**
    - **Answer**: Tools include the React DevTools, browser console logs, and breakpoints, along with tools like Redux DevTools for state inspection.

25. **What are common errors in React, and how do you handle them?**
    - **Answer**: Common errors include state updates on unmounted components, prop-type issues, and context conflicts. Solutions involve cleanup functions, `PropTypes`, and error boundaries.

### Section 6: Best Practices and Code Architecture

26. **How do you organize a large React application?**
    - **Answer**: Use folder structures that separate components, containers, services, hooks, and styles. Follow patterns like "atomic design" for consistency.

27. **What is an HOC, and when would you use it?**
    - **Answer**: A Higher-Order Component (HOC) is a function that takes a component and returns a new component. It's useful for reusing component logic, such as handling authentication or permissions.

28. **Explain the importance of keys in lists and how to use them correctly.**
    - **Answer**: Keys help React identify which items changed, are added, or are removed. They should be unique and stable to prevent unexpected re-renders.

29. **How do you implement conditional rendering in React?**
    - **Answer**: Use JavaScript conditional expressions like `&&`, ternary operators, and `if` statements inside JSX to render components based on specific conditions.

30. **What is the purpose of error boundaries?**
    - **Answer**: Error boundaries catch JavaScript errors in a component tree, preventing the entire app from crashing and enabling graceful fallbacks or error messages.

---

## Technical Task for Senior React Developer

### Task: Building a Todo List with Custom Hooks and Context API

#### Requirements:
1. Build a Todo list app where users can add, delete, and mark tasks as complete.
2. Use the Context API to manage the state across components.
3. Create custom hooks to add, delete, and toggle tasks.
4. Use React functional components and hooks only.

#### Solution

```javascript
// context/TodoContext.js
import React, { createContext, useState, useContext } from 'react';

const TodoContext = createContext();

export const TodoProvider = ({ children }) => {
  const [todos, setTodos] = useState([]);

  const addTodo = (task) => setTodos([...todos, { task, completed: false }]);
  const deleteTodo = (index) => setTodos(todos.filter((_, i) => i !== index));
  const toggleTodo = (index) => setTodos(
    todos.map((todo, i) =>
      i === index ? { ...todo, completed: !todo.completed } : todo
    )
  );

  return (
    <TodoContext.Provider value={{ todos, addTodo, deleteTodo, toggleTodo }}>
      {children}
    </TodoContext.Provider>
  );
};

export const useTodos = () => useContext(TodoContext);
/**********/
// hooks/useAddTodo.js
import { useTodos } from '../context/TodoContext';

export const useAddTodo = () => {
  const { addTodo } = useTodos();
  return addTodo;
};
/***/
// components/TodoList.js
import React from 'react';
import { useTodos } from '../context/TodoContext';

const TodoList = () => {
  const { todos, deleteTodo, toggleTodo } = useTodos();

  return (
    <ul>
      {todos.map((todo, index) => (
        <li key={index} style={{ textDecoration: todo.completed ? 'line-through' : 'none' }}>
          {todo.task}
          <button onClick={() => toggleTodo(index)}>Toggle</button>
          <button onClick={() => deleteTodo(index)}>Delete</button>
        </li>
      ))}
    </ul>
  );
};

export default TodoList;

/*****/
// App.js
import React, { useState } from 'react';
import { TodoProvider } from './context/TodoContext';
import TodoList from './components/TodoList';
import { useAddTodo } from './hooks/useAddTodo';

const App = () => {
  const [task, setTask] = useState('');
  const addTodo = useAddTodo();

  const handleAddTodo = () => {
    addTodo(task);
    setTask('');
  };

  return (
    <TodoProvider>
      <div>
        <h1>Todo List</h1>
        <input
          value={task}
          onChange={(e) => setTask(e.target.value)}
          placeholder="New Task"
        />
        <button onClick={handleAddTodo}>Add Task</button>
        <TodoList />
      </div>
    </TodoProvider>
  );
};

export default App;
```
### Explanation

- **The Context API** in TodoContext manages todo state across components.
- **Custom hooks** like useAddTodo allow separation of concerns, making the code more modular.
- Functional components and hooks implement task manipulation, demonstrating advanced React patterns.
