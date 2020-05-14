## BrowserRouter

[EN]

### Description

You are need to use **BrowserRouter** when you are process dynamic requests on the server.

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

### History

Every **Router** is creating `history` object that contains path on the current `location` and runs rerender UI when some changes on the path are happen.

Other functions provided by **React Router** are rely on the `history` object accessibility via  **context**, so it must render inside **Router** component.

>**Note**: 
>
>**React Router**'s components that haven't  **Router** component as parent element doesn't be work, because  **context** will not be available.

[RU]

### Описание

**BrowserRouter** следует использовать, когда вы обрабатываете на сервере динамические запросы.
 
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

### История

Каждый **Router** создает объект `history` который хранит путь к текущему `location` и перерисовывает интерфейс сайта когда происходят какие то изменения пути.

Остальные функции предоставляемые в **React Router** полагаются на доступность объекта `history` через  **context**, поэтому они должны рендериться внутри компонента **Router**.

>**Заметка**: 
>
>Компоненты **React Router**, не имеющие в качестве предка компонент **Router**, не будут работать, так как не будет доступен **context**.