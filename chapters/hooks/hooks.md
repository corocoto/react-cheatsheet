## What're Hooks? (Что такое хуки?)

[EN]

*Hooks* are a new addition in React 16.8. They let you use state and other React features without writing a class.

```jsx
import React, { useState } from 'react';

function Example() {
  // Declare a new state variable, which we'll call "count"
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>You clicked {count} times</p>
      <button onClick={() => setCount(count + 1)}>
        Click me
      </button>
    </div>
  );
}
```

[RU]

*Хуки* — нововведение в React 16.8, которое позволяет использовать состояние и другие возможности React без написания классов.

```jsx
import React, { useState } from 'react';

function Example() {
  // Объявление переменной состояния, которую мы назовём "count"
  const [count, setCount] = useState(0);

  return (
    <div>
      <p>Вы кликнули {count} раз</p>
      <button onClick={() => setCount(count + 1)}>
        Нажми на меня
      </button>
    </div>
  );
}
```