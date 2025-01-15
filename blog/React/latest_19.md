# What's New in React 19: Detailed Features and Code Examples

React 19 brings a host of new features designed to enhance performance, simplify development, and provide developers with more tools for building robust applications. Let's dive into these new additions, along with code examples to illustrate their usage.

---

## 1. React Compiler (RSC - React Server Compiler)

The React Compiler optimizes your code automatically during the build process. It performs tasks like memoization and efficient rendering without requiring manual intervention.

### Example:
Instead of manually using `useMemo` or `useCallback`:
```jsx
import React from 'react';

function ExpensiveComponent({ value }) {
  console.log('Re-rendering');
  return <div>{value}</div>;
}

export default function App() {
  const data = { key: 'value' };

  // React Compiler handles optimization for props
  return <ExpensiveComponent value={data} />;
}
```
In React 19, optimizations happen under the hood. No need to wrap `data` with `useMemo`.

---

## 2. Server Components

Server Components allow part of the React tree to render on the server, reducing the client-side bundle size and improving load times.

### Example:
```jsx
// Server Component (server.js)
export default function ServerComponent() {
  return <h1>This is rendered on the server</h1>;
}

// Client Component
import React from 'react';
import ServerComponent from './server';

export default function App() {
  return (
    <div>
      <ServerComponent />
    </div>
  );
}
```

This reduces client-side workload, leading to faster initial page loads.

---

## 3. Actions

Actions centralize state mutations and side effects, making data management more predictable.

### Example:
```jsx
'use server';

export async function submitForm(data) {
  // Server-side logic
  console.log(data);
  return { success: true };
}

// Client Component
import { submitForm } from './actions';

export default function App() {
  const handleSubmit = async (event) => {
    event.preventDefault();
    const formData = new FormData(event.target);
    const result = await submitForm(Object.fromEntries(formData));
    console.log(result);
  };

  return (
    <form onSubmit={handleSubmit}>
      <input name="username" placeholder="Enter your username" />
      <button type="submit">Submit</button>
    </form>
  );
}
```

---

## 4. Enhanced Asset Loading

React 19 allows you to preload assets like images and fonts in the background for smoother transitions.

### Example:
```jsx
import { preloadImage } from 'react';

export default function App() {
  const image = preloadImage('/path/to/image.jpg'); // Preloads the image

  return (
    <div>
      <img src={image} alt="Preloaded" />
    </div>
  );
}
```

---

## 5. Document Metadata Management

The `<DocumentHead>` component simplifies managing meta tags, titles, and other document-level metadata.

### Example:
```jsx
import { DocumentHead } from 'react';

export default function App() {
  return (
    <DocumentHead>
      <title>React 19 App</title>
      <meta name="description" content="Learn about React 19 features" />
    </DocumentHead>
  );
}
```

---

## 6. Improved Web Components Integration

React 19 improves interoperability with Web Components, making it easier to integrate custom elements.

### Example:
```jsx
function WebComponentWrapper() {
  return <my-web-component></my-web-component>;
}

export default function App() {
  return <WebComponentWrapper />;
}
```

---

## 7. New and Enhanced Hooks

### **a. `useOptimistic()`**
Optimistic updates are now more straightforward.

```jsx
import { useOptimistic } from 'react';

function LikeButton() {
  const [isLiked, setIsLiked] = useOptimistic(false);

  const handleClick = () => {
    setIsLiked(true);
    // Simulate server confirmation
    setTimeout(() => console.log('Server updated'), 2000);
  };

  return <button onClick={handleClick}>{isLiked ? 'Liked' : 'Like'}</button>;
}
```

---

### **b. `useFormStatus()`**
Easily access form state in child components.

```jsx
import { useFormStatus } from 'react';

function SubmitButton() {
  const { pending } = useFormStatus();
  return <button disabled={pending}>{pending ? 'Submitting...' : 'Submit'}</button>;
}

export default function Form() {
  return (
    <form>
      <input name="email" placeholder="Enter your email" />
      <SubmitButton />
    </form>
  );
}
```

---

### **c. `useActionState()`**
Track the state of asynchronous actions.

```jsx
import { useActionState } from 'react';

export default function App() {
  const [actionState, startAction] = useActionState();

  const handleAction = () => {
    startAction(async () => {
      console.log('Performing action...');
      await new Promise((resolve) => setTimeout(resolve, 2000));
      console.log('Action completed');
    });
  };

  return (
    <div>
      <button onClick={handleAction} disabled={actionState.pending}>
        {actionState.pending ? 'Loading...' : 'Click Me'}
      </button>
    </div>
  );
}
```

---

### **d. `use()`**
Fetch data directly in components without `useEffect`.

```jsx
import { use } from 'react';

async function fetchData() {
  return { data: 'Hello, world!' };
}

export default function App() {
  const data = use(fetchData());
  return <div>{data.data}</div>;
}
```

---

React 19 makes building high-performance, scalable applications more intuitive and enjoyable. From new hooks to improved server-side capabilities, there's a lot to explore.
