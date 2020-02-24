### `useState`

#### Introduction

`useState` is a hook that allows you to have state variables in functional components.

**Notice**: Since React 16.8 we can use hooks, which are functions with names starting with `use`, to add state variables to functional components and instrument the lifecycle methods of classes.

The `useState` (state) hook is equivalent of `this.state`/`this.setSate` for functional components.

#### Declare this `hook`

1. `useState` is a named `export` from `react` so to use it, you can write:
```jsx
React.useState
```
2. Import it just write `useState`:
```jsx
import React, { useState } from 'react';
```

#### What it contains inside?
`useState` doesn’t return just a variable. It returns an `array`, where the first element is the state variable and the second element is a `function` to update the value of the variable. 
For such cases, commonly used **array destructuring**:

```jsx
const [personsState, setPersonsState] = useState({
    persons: [
        {name: "Max", age: 29},
        {name: "Andrew", age: 22},
        {name: "Alice", age: 25}
    ]
});
```

At example above `pesonState` contains next structure (initial state):

```jsx
persons: [
    {name: "Max", age: 29},
    {name: "Andrew", age: 22},
    {name: "Alice", age: 25}
]
```

And `setPersonsState` contains function, which allows update this state. We may say, that `setPersonsState` function is equal `this.setState` at class-based component.

#### What you need to pay attention?
1. `useState` can be used repeatedly. What am I mean?
```jsx
const [personsState, setPersonsState] = useState({
    persons: [
        {name: "Max", age: 29},
        {name: "Andrew", age: 22},
        {name: "Alice", age: 25}
    ]
});

const [otherState, setOtherState] = useState({
    other: 'some other value'
});

```

2. Unlike `this.setState` in class components, `useState` doesn’t merge objects when the state is updated. It replaces them.

```jsx
/* after that, personState will object, which contains persons and otherState properties */

const [personsState, setPersonsState] = useState({
    persons: [
        {name: "Max", age: 29},
        {name: "Andrew", age: 22},
        {name: "Alice", age: 25}
    ],
    otherState: 'some other value'
});


/*after that, personState will object, which contains persons property only*/
setPersonState({
    [
        {name: "Maximilian", age: 29},
        {name: "Andrew", age: 22},
        {name: "Alice", age: 24}
    ]
});
```