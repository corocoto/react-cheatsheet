## withRouter

[EN]

### Description

Thanks to **withRouter** HOC you can get access for **match**, **location**, and **history** inside of functional component. 
It's super important when you work with routes inside of it.
 
Because you can get access for this props inside class-based component, and you don't need to use some tools or something else for that. 
But inside of functional component you can't get access for it at default.

**Example**:

```jsx
import React from 'react';
import {withRouter} from 'react-router-dom';

// A simple component that shows the pathname of the current location
const ShowTheLocation = (props) => {
    const { match, location, history } = this.props;
    return <div>You are now at {location.pathname}</div>;
}

export default withRouter(ShowTheLocation);
```

[RU]

### Описание

Благодаря HOC'у **withRouter**, вы можете можете получить доступ к **match**, **location**, **history** внутри функционального компонента.
Это очень важно в тот момент, когда вы работаете с маршрутами внутри этого компонента.

Так как вы можете получит доступ к этим пропсам внутри классового компонента, и для этого вам не нужно использовать какие-либо инструменты или что-либо еще. 
Но внутри функционального компонента вы не сможете получить доступ к ним по умолчанию. 

**Пример**:

```jsx
import React from 'react';
import {withRouter} from 'react-router-dom';

// Простой компонент, который показывает путь текущей локации
const ShowTheLocation = (props) => {
    const { match, location, history } = this.props;
    return <div>You are now at {location.pathname}</div>;
}

export default withRouter(ShowTheLocation);
```