### useEffect

`useEffect` allows us to running side effects at functional component:

>**Note** 
>If you know about class lifecycle methods, so `useEffect` hook present combine of `componentDidMount` and `componentDidUpdate` methods.
>So we can tell, that `useEffect` will running after render.

For more understandable, let look an example of class-based component and functional component, that will doing same things. Also we trying compare it, and finding differences between.

### Effects without reset

**Example 1:**

* **class-based component**:

```jsx
class Example extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      count: 0
    };
  }

  componentDidMount() {
    document.title = `Вы нажали ${this.state.count} раз`;
  }

  componentDidUpdate() {
    document.title = `Вы нажали ${this.state.count} раз`;
  }

  render() {
    return (
      <div>
        <p>Вы нажали {this.state.count} раз</p>
        <button onClick={() => this.setState({ count: this.state.count + 1 })}>
          Нажми на меня
        </button>
      </div>
    );
  }
}
```

>**Note:** We can see, that code are doubling (looks on code `componentDidMount` and `componentDidUpdate` methods). It's not good. But we have alternative.

* **functional component**:

```jsx
import React, { useState, useEffect } from 'react';

function Example() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    document.title = `Вы нажали ${count} раз`;
  });

  return (
    <div>
      <p>Вы нажали {count} раз</p>
      <button onClick={() => setCount(count + 1)}>
        Нажми на меня
      </button>
    </div>
  );
}
```


It's looks like better. 
>**So what `useEffect` doing?**
>You're talking to React, that it's doing something after render, using this hook. 
>React is remember function (i.e. "effect"), that you send and run it after making all changes to the DOM.


### Effects with reset

We are looking side effects, that don't take reset early. However, there are cases, when reset is necessary. As example, we are may to need listener on something external data source. In this case, it's very important to run reset, so that there is no memory leaks.

Let's looks examples, that realised it:

* **class-based component**:

```jsx
class FriendStatus extends React.Component {
  constructor(props) {
    super(props);
    this.state = { isOnline: null };
    this.handleStatusChange = this.handleStatusChange.bind(this);
  }

  componentDidMount() {
    ChatAPI.subscribeToFriendStatus(
      this.props.friend.id,
      this.handleStatusChange
    );
  }

  componentWillUnmount() {
    ChatAPI.unsubscribeFromFriendStatus(
      this.props.friend.id,
      this.handleStatusChange
    );
  }

  handleStatusChange(status) {
    this.setState({
      isOnline: status.isOnline
    });
  }

  render() {
    if (this.state.isOnline === null) {
      return 'Загрузка...';
    }
    return this.state.isOnline ? 'В сети' : 'Не в сети';
  }
}
```

>At React class, usually, set listener at `componentDidMount` and reset it at `componentWillUnmount`.

* **functional component**

Let's looks, how this component be view, if it will be writes using hooks.

```jsx
import React, { useState, useEffect } from 'react';

function FriendStatus(props) {
  const [isOnline, setIsOnline] = useState(null);

  useEffect(() => {
    function handleStatusChange(status) {
      setIsOnline(status.isOnline);
    }

    ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
    // Указываем, как сбросить этот эффект:
    return function cleanup() {
      ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
    };
  });

  if (isOnline === null) {
    return 'Загрузка...';
  }
  return isOnline ? 'В сети' : 'Не в сети';
}
```

>**Note:** If your effect is return a function, so React run it only, when the time comes to reset the effect.

### Advice: performance optimization by skipping effects

In some cases a reset or running effect by every render may to call a problem with performance. At class-based components, we can resolve it to using additional compare `prevProps` or `prevState` inside `componentDidUpdate`:

```jsx
componentDidUpdate(prevProps, prevState) {
  if (prevState.count !== this.state.count) {
    document.title = `Вы нажали ${this.state.count} раз`;
  }
}
```

But it'll be running inside of class-based component, but not functional component.
But functional component has same thing. It contains inside of `useEffect` hook. 
You can do so, that React missed call effect, if certain values ​​remain unchanged between subsequent renders.

For doing it, pass the array to `useEffect` as second optional argument.

```jsx
useEffect(() => {
  document.title = `Вы нажали ${count} раз`;
}, [count]); // Перезапускать эффект только если count поменялся
```

>**Note**: In this example, we pass `[count]` as second argument. 
>
>What is it mean? 
>It's mean, that if `count` will equal `5` and our component re-rendered with same value (`count` = `5`). React will compare `[5]` from previous render and `[5]` from next render. As, all array elements remain without changing, so React misses this effect. It's an optimization of this process.
>
>When our variable `count` updates to `6` on the next render, React compare the array elements `[5]` from previous render and the array elements `[6]` from next render. In this case, React runs  our effect, because `5 !== 6`.
>
>If you have some elements in array, React will running pur effect, on the time, when one of the elements will be change.

It's also work for effect with reset step:

```jsx
useEffect(() => {
  function handleStatusChange(status) {
    setIsOnline(status.isOnline);
  }

  ChatAPI.subscribeToFriendStatus(props.friend.id, handleStatusChange);
  return () => {
    ChatAPI.unsubscribeFromFriendStatus(props.friend.id, handleStatusChange);
  };
}, [props.friend.id]); // Повторно подписаться, только если props.friend.id изменился
```