## `useRef`

[EN]

`useRef` allows us using refs for functional components.

Let's looks an example how it works: 

```jsx
import React, {useEffect, useRef} from "react";
import classes from "./Cockpit.module.css";

const Cockpit = (props) => {

    //init ref and set initial value for it
    const btnRef = useRef(null);

    useEffect(()=>{
        //run click after first render
        btnRef.current.click();
    }, []);
    const assignClasses = [];
    if (props.personsLength < 3) {
        assignClasses.push(classes.red);
    }
    if (props.personsLength < 2) {
        assignClasses.push(classes.bold);
    }
    return (
        <React.Fragment>
            <h1>
                {props.title}
            </h1>
            <p className={assignClasses.join(' ')}> And it's work</p>
            <button
                className={classes.button}
                ref={btnRef}
                alt={props.show ? 'show' : undefined}
                onClick={props.clicked}>
                Toggle Persons
            </button>
        </React.Fragment>)
};

export default React.memo(Cockpit);
```

[RU]

`useRef` позволяет нам использовать ref'ы в функциональных компонентах.

Давайте рассмотрим пример того, как это работает: 

```jsx
import React, {useEffect, useRef} from "react";
import classes from "./Cockpit.module.css";

const Cockpit = (props) => {

    //инициализируем ref и устанавливаем первоначальное значение для него
    const btnRef = useRef(null);

    useEffect(()=>{
        //запускаем вызвов клика после первой отрисовки
        btnRef.current.click();
    }, []);
    const assignClasses = [];
    if (props.personsLength < 3) {
        assignClasses.push(classes.red);
    }
    if (props.personsLength < 2) {
        assignClasses.push(classes.bold);
    }
    return (
        <React.Fragment>
            <h1>
                {props.title}
            </h1>
            <p className={assignClasses.join(' ')}> And it's work</p>
            <button
                className={classes.button}
                ref={btnRef}
                alt={props.show ? 'show' : undefined}
                onClick={props.clicked}>
                Toggle Persons
            </button>
        </React.Fragment>)
};

export default React.memo(Cockpit);
```