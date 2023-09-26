# Below are some common code snips:

## React:

### Create a counter

```jsx
import { useState }  'react';

const Counter = () => {
    const [counter, setCounter] = useState(0);
};

const handleClick = () => {
    setCounter(counter + 1);
};

return (
    <>
        <p>{counter}</p>
        <button onClick = {handleClick}>Count</button>
        <button onClick = {() => setCounter(0)}>Reset</button>
    </>
)
```
