# useCallback
The **useCallback hook** in React is used to **memoize functions**, **preventing unnecessary re-renders** in child components that rely on these functions. It's particularly useful when passing callbacks to child components, as it ensures that the callback reference remains stable across renders if the dependencies have not changed. This can help optimize performance, especially in scenarios where child components are memoized using **React.memo**.



