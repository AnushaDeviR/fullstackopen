# A more complex state, debugging React apps

## Complex state

- For applications that needs a more complex state, an optimal way to achieve this is to use `useState` function multiple times to create separate pieces of state.

```js
import React, { useState } from "react";

const MoreCounters = () => {
  const [left, setLeft] = useState(0);
  const [right, setRight] = useState(0);

  const handleLeft = () => {
    setLeft(left + 1);
  };

  const handleRight = () => {
    setRight(right + 1);
  };
  return (
    <div>
      <h3>Applying complex states</h3>
      <div>
        {left}
        <button onClick={handleLeft}>Left Counter</button>
      </div>
      <div>
        {right}
        <button onClick={handleRight}>Right Counter</button>
      </div>
    </div>
  );
};

export default MoreCounters;
```

// 👆🏼 can also be written as:

```js
const [clicks, setClicks] = useState({
  left: 0,
  right: 0,
});

const handleLeftClicks = () => {
  const newClicks = {
    ...clicks,
    left: clicks.left + 1,
  };
  setClicks(newClicks);
};

const handleRightClicks = () => {
  const newClicks = {
    ...clicks,
    right: clicks.right + 1,
  };
  setClicks(newClicks);
};
```
