## `useState`

[EN]

#### Introduction

`useState` is a hook that allows you to have state variables in functional components.

**Notice**: Since React 16.8 we can use hooks, which are functions with names starting with `use`, to add state variables to functional components and instrument the lifecycle methods of classes.

The `useState` (state) hook is equivalent of `this.state`/`this.setSate` for functional components.

#### Declare this hook

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

At example above `pesonsState` contains next structure (initial state):

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

[RU]

#### Введение

`useState` - это хук, который позволяет вам иметь переменную состояния в функциональных компонентах.

**Примечание**: Начиная с версии React 16.8  мы можем использовать хуки, которые являются функциями с именами, начинающимися с `use`, которые добавляют переменные состояния в функциональные компоненты и инструмент методов жизненного цикла классов.

`useState` (state) хук эвивалентен `this.state`/`this.setSate`, использующийся для функциональных компонентов.

#### Объявление этого хука

1. `useState` является именнованным значением из `export`'а  `react`, поэтому для того, чтобы использовать его, вы можете написать:
```jsx
React.useState
```
2. Импортирование `useState`:
```jsx
import React, { useState } from 'react';
```

#### Что он содержит внутри?

`useState` не возвращает просто переменную. Он возвращает `массив`, где первый элемент - это состояние переменной, а второй - `функция` для обновления значения переменной. 
Для таких случаев обычно используется  **деструктуризация массива**:

```jsx
const [personsState, setPersonsState] = useState({
    persons: [
        {name: "Max", age: 29},
        {name: "Andrew", age: 22},
        {name: "Alice", age: 25}
    ]
});
```

В примере выше `pesonsState` содержит следующую структуру (первоначальное состояние):

```jsx
persons: [
    {name: "Max", age: 29},
    {name: "Andrew", age: 22},
    {name: "Alice", age: 25}
]
```

А `setPersonsState` содержит внутри себя функцию, которая позволяет обновлять это состояние. Мы можем сказать, что функция `setPersonsState` идентична `this.setState` в классовом компоненте.

#### На что вам необходимо обратить внимание ?
1. `useState` может быть использован повторно. Что я имею в виду?

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

2. В отличие от `this.setState` в классовых компонентах, `useState` не объединяет объекты , когда состояние обновилось. Оно заменяет их.

```jsx
/* после этого personState будет объектом, который содержит свойства persons и otherState */

const [personsState, setPersonsState] = useState({
    persons: [
        {name: "Max", age: 29},
        {name: "Andrew", age: 22},
        {name: "Alice", age: 25}
    ],
    otherState: 'some other value'
});


/* после этого personState будет объектом, содержащим только свойство persons */
setPersonState({
    [
        {name: "Maximilian", age: 29},
        {name: "Andrew", age: 22},
        {name: "Alice", age: 24}
    ]
});
```
