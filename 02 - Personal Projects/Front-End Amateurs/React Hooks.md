2024/10/04 12:09
Status: #idea
Tags:

# React Hooks Lesson: useState and useEffect

**Duration:** 30 minutes

## Objectives:
By the end of this section, students will be able to:
1. Understand and implement the useState hook
2. Understand and implement the useEffect hook
3. Recognize common use cases for these hooks

## I. Introduction to Hooks (2 minutes)
- Brief explanation of what hooks are and why they're useful
- Mention that we'll focus on useState and useEffect

## II. useState Hook (13 minutes)

### Explanation (3 minutes)
- Purpose: Managing state in functional components
- Syntax: `const [state, setState] = useState(initialValue);`

### Example: Counter Component (10 minutes)

Live coding: Create a simple counter component using useState

```jsx
import React, { useState } from 'react';

function Counter() {
  const [count, setCount] = useState(0);

  const increment = () => {
    setCount(count + 1);
  };

  return (
    <div>
      <p>Count: {count}</p>
      <button onClick={increment}>Increment</button>
    </div>
  );
}

export default Counter;
```

- Walk through the code, explaining:
  - How useState is initialized
  - How the state is updated using setCount
  - How the state is displayed in the JSX

- Demonstrate the component in action
- Encourage students to modify the code (e.g., add a decrement button)

## III. useEffect Hook (15 minutes)

### Explanation (3 minutes)
- Purpose: Handling side effects in components
- Common use cases: data fetching, subscriptions, manual DOM manipulations
- Syntax: `useEffect(() => { // effect }, [dependencies]);`

### Example: Fetching Data with useEffect (12 minutes)

Live coding: Create a component that fetches and displays a random joke

```jsx
import React, { useState, useEffect } from 'react';

function RandomJoke() {
  const [joke, setJoke] = useState('');
  const [isLoading, setIsLoading] = useState(true);

  useEffect(() => {
    fetchJoke();
  }, []);

  const fetchJoke = async () => {
    setIsLoading(true);
    try {
      const response = await fetch('https://api.chucknorris.io/jokes/random');
      const data = await response.json();
      setJoke(data.value);
    } catch (error) {
      console.error('Error fetching joke:', error);
      setJoke('Failed to fetch joke. Please try again.');
    }
    setIsLoading(false);
  };

  return (
    <div>
      <h2>Random Joke</h2>
      {isLoading ? (
        <p>Loading...</p>
      ) : (
        <>
          <p>{joke}</p>
          <button onClick={fetchJoke}>Get New Joke</button>
        </>
      )}
    </div>
  );
}

export default RandomJoke;
```

- Walk through the code, explaining:
  - How useEffect is used to fetch data when the component mounts
  - The use of multiple state variables (joke and isLoading)
  - How to handle loading states and errors
  - The empty dependency array `[]` to run the effect only once

- Demonstrate the component in action
- Show how removing the dependency array causes issues (joke fetched on every render)
- Discuss the importance of properly managing effects to avoid unnecessary re-renders

## IV. Wrap-up and Q&A (2 minutes)
- Recap the key points about useState and useEffect
- Address any questions from students
- Encourage students to experiment with these hooks in their own projects






---
# References
