## BrowserRouter

[EN]

**React Router** provides you with a component that is one of the types of router - this is **BrowserRouter**.

You are need to using it when you are process  dynamic requests on the server.

You are need to importing it from the [`react-router-dom`](react-router-dom.md) package for you're begin using it.

 ```js
import {BrowserRouter} from 'react-router-dom';
 ```

Usually, it's a wrapper whole project.

Example:
```jsx
//index.js 
import React from 'react';
import ReactDOM from 'react-dom';
import {BrowserRouter} from 'react-router-dom';
import './index.css';
import App from './App';
import * as serviceWorker from './serviceWorker';
const app = (
    <BrowserRouter>
        <React.StrictMode>
            <App />
        </React.StrictMode>
    </BrowserRouter>
);
ReactDOM.render(app, document.getElementById('root'));
serviceWorker.unregister();
```

[RU]

**React Router** предоставляет вам компонент, являющийся одим из типов роутеров - это  **BrowserRouter**.

Его следует использовать когда вы обрабатываете на сервере динамические запросы.
 
Для того, чтобы начать его использование, нужно импортровать его из пакета [`react-router-dom`](react-router-dom.md).
 
 ```js
import {BrowserRouter} from 'react-router-dom';
 ```
 
Обычно им обрачивают весь проект.
 
Пример:
 
 ```jsx
//index.js 
import React from 'react';
import ReactDOM from 'react-dom';
import {BrowserRouter} from 'react-router-dom';
import './index.css';
import App from './App';
import * as serviceWorker from './serviceWorker';
const app = (
    <BrowserRouter>
        <React.StrictMode>
            <App />
        </React.StrictMode>
    </BrowserRouter>
);
ReactDOM.render(app, document.getElementById('root'));
serviceWorker.unregister();
```