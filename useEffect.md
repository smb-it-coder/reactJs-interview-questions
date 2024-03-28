# useEffect
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
### Dependency Array:
You can provide a second argument to useEffect, which is an array of dependencies. The effect will only re-run if any of the dependencies have changed between renders.

                  useEffect(() => {
                    // This function will run only when 'count' changes
                    document.title = `You clicked ${count} times`;
                  }, [count]); // Dependency array
### Cleanup:
useEffect can also return a cleanup function. This function will be executed before the component unmounts or before the effect runs again due to a re-render.

      useEffect(() => {
        // Subscribe to some external data source
        const subscription = externalDataSource.subscribe(data => {
          // Update component state
        });
      
        // Cleanup function
        return () => {
          // Unsubscribe from the data source when component unmounts
          subscription.unsubscribe();
        };
      }, []); // No dependencies, so cleanup runs only on unmount

### Rules of useEffect:
 - **1** Effects run after every render by default.
 - **2** Effects with a dependency array only re-run if dependencies have changed.
- **3** Effects with a cleanup function will run that cleanup before applying the next effect.
- **4** You cannot directly return a promise from useEffect. Instead, you can create an async function inside and call it.

            useEffect(() => {
              async function fetchData() {
                const response = await fetch('api/data');
                const data = await response.json();
                // Update component state
              }
              fetchData();
            }, []);


## Common Use Cases:

- Fetching data from an API when a component mounts.
- Subscribing to external data sources.
- Manipulating the DOM directly.
- Setting up event listeners.
- Managing document titles or other side effects.

**useEffect** is a powerful hook that enables you to handle side effects in function components effectively, providing cleaner and more concise code compared to class components' lifecycle methods. Understanding its usage and the rules around it is crucial for building React applications efficiently.
