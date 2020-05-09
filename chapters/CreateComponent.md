## Creating component (Создание компонента)

[EN]

React.js library allows us to create components in two different ways:

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


[RU]

Библиотека React.js позволяет нам создвать компоненты двумя разными способами:

1. С помощью `jsx` синтаксиса:
  ```jsx
    return (
      <div className="App">
        <h1>Hi, I am a React-App</h1>
      </div>
    );
  ```

2. Используя метод `createElement`:
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

**Примечание**. Примеры выше будут иметь одинаковый результат.