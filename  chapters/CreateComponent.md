### React.js library allows us to create component in two different ways:

1. `jsx`-syntax: 
  ```jsx
    return (
      <div className="App">
        <h1>Hi, I am a React-App</h1>
      </div>
    );
  ```
  
2. Using `createElement` method: 
```js
  return React.createElement(
    'div',
     { className: 'App' },
     React.createElement(
      'h1',
      null,
      'Hi, I am a React-App')
  );
```

**Notice**. Examples above will have the same (equal) result. 