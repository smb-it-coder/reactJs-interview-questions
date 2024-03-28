The **useEffect hook** in React is used for performing side effects in function components. Side effects may include data fetching, subscriptions, or manually changing the DOM in reaction to state or props changes. useEffect is a replacement for lifecycle methods like **componentDidMount**, **componentDidUpdate**, and **componentWillUnmount** in class components.

## Basic Usage:

      import React, { useState, useEffect } from 'react';
      
      function MyComponent() {
        const [count, setCount] = useState(0);
      
        useEffect(() => {
          // This function will run after every render
          document.title = `You clicked ${count} times`;
        });
      
        return (
          <div>
            <p>You clicked {count} times</p>
            <button onClick={() => setCount(count + 1)}>
              Click me
            </button>
          </div>
        );
      }

In this example, the effect specified inside **useEffect** runs after every render because it does not have a second argument. This is equivalent to **componentDidMount** and **componentDidUpdate** lifecycle methods combined in class components.



