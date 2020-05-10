## Using pseudo classes, pseudo elements and media queries in inline styles (Использование псевдоклассов, псевдоэлементов и медиа выражений в inline-стилях)

[EN]

For possibility to adding and using pseudo classes, pseudo elements or maybe media queries, you are need to install the [radium](https://www.npmjs.com/package/radium) package, which allows doing it.

For install this package, you're need to using next command:

```bash
$ npm install radium
```

After that, we are necessary to importing this package on that file, on which we are want to add pseudo classes, pseudo elements or media queries. As example, it file is `App.js`:

```jsx
import React, {Component} from 'react';
import './App.css';
import Radium from 'radium';
import Person from './Person/Person';
```

At the end of this file (where we are exporting component), we are need to wrap **App** component into **Radium**:

```jsx
export default Radium(App);
```

Next step is adding styles. Let's take a look on the part of App component's code: 

```jsx
import React, {Component} from 'react';
import './App.css';
import Radium from 'radium';
import Person from './Person/Person';

class App extends Component {
    constructor(props) {
        super(props);
        this.state = {
            persons: [
                {id: '172',name: "Max", age: 29},
                {id: '123',name: "Andrew", age: 22},
                {id: '129', name: "Alice", age: 25}
            ],
            showPersons: false
        }
    }

    switchNameHandler = (newName) => {
        this.setState({
            persons: [
                {name: newName, age: 29},
                {name: "Andrew", age: 22},
                {name: "Alice", age: 24}
            ]
        });
    };

    togglePersonsHandler = () => {
        const currentShowPersonsVal = this.state.showPersons;
        this.setState({
            showPersons: !currentShowPersonsVal
        });
    };

    render() {
        const style = {
            backgroundColor: 'green',
            color: 'white',
            font: 'inherit',
            padding: '8px',
            border: '1px solid blue',
            borderRadius: '4px',
            /* the ability to write such syntax is provided by the radium package */
            /* in this case, we are add styles for hover effect */
            ':hover': {
                backgroundColor: 'lightgreen',
                color: 'black'
            }
        };
        let persons = null;
        if (this.state.showPersons){
            persons = (
                <div>
                {this.state.persons.map((person, index)=>{
                    return <Person
                        key={person.id}
                        name={person.name}
                        age={person.age}
                        />}
                )}
                </div>
            );

            style.backgroundColor ='red';
            /*same situation*/
            style[':hover'] = {
                backgroundColor: 'darkred',
                color: 'black'
            }
        }

        return (
            <div className="App">
                <h1>
                    Hi, I am a React-App
                </h1>
                <p>And it's work</p>
                <button
                    style={style}
                    onClick={this.togglePersonsHandler}>
                    Toggle Persons
                </button>
                {persons}
            </div>
        );
    }

};

export default Radium(App);
```

### Using media queries

For writing media queries using `radium` package you're need to write syntax as example bellow:

```jsx
const style = {
    '@media (min-width : 500px)': {
        width: '400px'
    }
};
```

Let's take a look on how add media queries for **Person** component:

```jsx
import React from "react";
import Radium from 'radium';
import './Person.css';

const Person = (props) => {
    const style = {
        '@media (min-width : 500px)': {
            width: '400px'
        }
    };
    return (
        <div className="Person" style={style}>
            <h2 onClick={props.onClick} >I'm {props.name} and I'm {props.age} years old!</h2>
            {props.children && <p>{props.children}</p>}
            <input type="text" onChange={props.onChange} value={props.name}/>
        </div>);
};

export default Radium(Person);
```

If we are using media queries, so we also must be loading **StyleRoot**.
Let's take to add it into `App.js` file. And wrap our html structure into it:

```jsx
import React, {Component} from 'react';
import './App.css';
import Radium, {StyleRoot} from 'radium';
import Person from './Person/Person';

class App extends Component {
    constructor(props) {
        super(props);
        this.state = {
            persons: [
                {id: '172',name: "Max", age: 29},
                {id: '123',name: "Andrew", age: 22},
                {id: '129', name: "Alice", age: 25}
            ],
            showPersons: false
        }
    }

    switchNameHandler = (newName) => {
        this.setState({
            persons: [
                {name: newName, age: 29},
                {name: "Andrew", age: 22},
                {name: "Alice", age: 24}
            ]
        });
    };

    changeEventHandler(event, id){
        const personIndex = this.state.persons.findIndex(person=>person.id === id);
        const person = {
            ...this.state.persons[personIndex]
        };
        person.name = event.target.value;

        const persons = [...this.state.persons];
        persons[personIndex] = person;
        this.setState({persons});
    }

    togglePersonsHandler = () => {
        const currentShowPersonsVal = this.state.showPersons;
        this.setState({
            showPersons: !currentShowPersonsVal
        });
    };

    deleteEventHandler(personIndex){
        const persons = [...this.state.persons];
        persons.splice(personIndex,1);
        this.setState({persons})
    }

    render() {
        const style = {
            backgroundColor: 'green',
            color: 'white',
            font: 'inherit',
            padding: '8px',
            border: '1px solid blue',
            borderRadius: '4px',
            ':hover': {
                backgroundColor: 'lightgreen',
                color: 'black'
            }
        };
        let persons = null;
        if (this.state.showPersons){
            persons = (
                <div>
                {this.state.persons.map((person, index)=>{
                    return <Person
                        key={person.id}
                        name={person.name}
                        age={person.age}
                        onClick={this.deleteEventHandler.bind(this,index)}
                        onChange={event => this.changeEventHandler(event, person.id)}
                        />}
                )}
                </div>
            );

            style.backgroundColor ='red';
            style[':hover'] = {
                backgroundColor: 'darkred',
                color: 'black'
            }
        }
        const classes = [];
        if (this.state.persons.length < 3){
            classes.push('red');
        }
        if (this.state.persons.length < 2){
            classes.push('bold');
        }

        return (
            <!--we use `StyleRoot` so that we media queries take effect -->
            <StyleRoot>
                <div className="App">
                    <h1>
                        Hi, I am a React-App
                    </h1>
                    <p className={classes.join(' ')}>And it's work</p>
                    <button
                        style={style}
                        onClick={this.togglePersonsHandler}>
                        Toggle Persons
                    </button>
                    {persons}
                </div>
            </StyleRoot>
        );
    }

};

export default Radium(App);
```

[RU]

Для возможности добавления и использования псевдоклассов, псевдоэлементов или возможно медиа выражений, вам необходимо установить пакет [radium](https://www.npmjs.com/package/radium), который позволяет делать это.

Для установки этого пакета, вам нужно использовать следующую команду:

```bash
$ npm install radium
```

Поcле этого, нам необходимо импортировать этот пакет  в файл, в котором мы хотим добавить псевдоклассы, псевдоэлементы или медиа выражения. Например, этим файлом является `App.js`:

```jsx
import React, {Component} from 'react';
import './App.css';
import Radium from 'radium';
import Person from './Person/Person';
```

В конце этого файла (где мы экспортим компонент), нам нужно обернуть компонент **App** в **Radium**:

```jsx
export default Radium(App);
```

Следующий шаг - добавление стилей. Давайте посмотрим на часть кода компонента **App**: 

```jsx
import React, {Component} from 'react';
import './App.css';
import Radium from 'radium';
import Person from './Person/Person';

class App extends Component {
    constructor(props) {
        super(props);
        this.state = {
            persons: [
                {id: '172',name: "Max", age: 29},
                {id: '123',name: "Andrew", age: 22},
                {id: '129', name: "Alice", age: 25}
            ],
            showPersons: false
        }
    }

    switchNameHandler = (newName) => {
        this.setState({
            persons: [
                {name: newName, age: 29},
                {name: "Andrew", age: 22},
                {name: "Alice", age: 24}
            ]
        });
    };

    togglePersonsHandler = () => {
        const currentShowPersonsVal = this.state.showPersons;
        this.setState({
            showPersons: !currentShowPersonsVal
        });
    };

    render() {
        const style = {
            backgroundColor: 'green',
            color: 'white',
            font: 'inherit',
            padding: '8px',
            border: '1px solid blue',
            borderRadius: '4px',
            /* возможность написания такого синтаксиса предосталяется пакетом radium */
            /* в данном случае, мы добавляем стили для hover-эффекта */
            ':hover': {
                backgroundColor: 'lightgreen',
                color: 'black'
            }
        };
        let persons = null;
        if (this.state.showPersons){
            persons = (
                <div>
                {this.state.persons.map((person, index)=>{
                    return <Person
                        key={person.id}
                        name={person.name}
                        age={person.age}
                        />}
                )}
                </div>
            );

            style.backgroundColor ='red';
            /*same situation*/
            style[':hover'] = {
                backgroundColor: 'darkred',
                color: 'black'
            }
        }

        return (
            <div className="App">
                <h1>
                    Hi, I am a React-App
                </h1>
                <p>And it's work</p>
                <button
                    style={style}
                    onClick={this.togglePersonsHandler}>
                    Toggle Persons
                </button>
                {persons}
            </div>
        );
    }

};

export default Radium(App);
```

### Использование медиа выражений

Для написания медиа выражений, используя для этого пакет `radium`, вам необходимо следовать синтаксису, показанному в примере ниже:

```jsx
const style = {
    '@media (min-width : 500px)': {
        width: '400px'
    }
};
```

Давайте посмотрим, как писать медиа выражения для компонента **Person**:

```jsx
import React from 'react';
import Radium from 'radium';
import './Person.css';

const Person = (props) => {
    const style = {
        '@media (min-width : 500px)': {
            width: '400px'
        }
    };
    return (
        <div className="Person" style={style}>
            <h2 onClick={props.onClick} >I'm {props.name} and I'm {props.age} years old!</h2>
            {props.children && <p>{props.children}</p>}
            <input type="text" onChange={props.onChange} value={props.name}/>
        </div>);
};

export default Radium(Person);
```

Если мы используем медиа выражения, мы также должны подгружать **StyleRoot**.
Давайте добавим его в `App.js` файл. И обернем нашу html-структуру в нем:

```jsx
import React, {Component} from 'react';
import './App.css';
import Radium, {StyleRoot} from 'radium';
import Person from './Person/Person';

class App extends Component {
    constructor(props) {
        super(props);
        this.state = {
            persons: [
                {id: '172',name: "Max", age: 29},
                {id: '123',name: "Andrew", age: 22},
                {id: '129', name: "Alice", age: 25}
            ],
            showPersons: false
        }
    }

    switchNameHandler = (newName) => {
        this.setState({
            persons: [
                {name: newName, age: 29},
                {name: "Andrew", age: 22},
                {name: "Alice", age: 24}
            ]
        });
    };

    changeEventHandler(event, id){
        const personIndex = this.state.persons.findIndex(person=>person.id === id);
        const person = {
            ...this.state.persons[personIndex]
        };
        person.name = event.target.value;

        const persons = [...this.state.persons];
        persons[personIndex] = person;
        this.setState({persons});
    }

    togglePersonsHandler = () => {
        const currentShowPersonsVal = this.state.showPersons;
        this.setState({
            showPersons: !currentShowPersonsVal
        });
    };

    deleteEventHandler(personIndex){
        const persons = [...this.state.persons];
        persons.splice(personIndex,1);
        this.setState({persons})
    }

    render() {
        const style = {
            backgroundColor: 'green',
            color: 'white',
            font: 'inherit',
            padding: '8px',
            border: '1px solid blue',
            borderRadius: '4px',
            ':hover': {
                backgroundColor: 'lightgreen',
                color: 'black'
            }
        };
        let persons = null;
        if (this.state.showPersons){
            persons = (
                <div>
                {this.state.persons.map((person, index)=>{
                    return <Person
                        key={person.id}
                        name={person.name}
                        age={person.age}
                        onClick={this.deleteEventHandler.bind(this,index)}
                        onChange={event => this.changeEventHandler(event, person.id)}
                        />}
                )}
                </div>
            );

            style.backgroundColor ='red';
            style[':hover'] = {
                backgroundColor: 'darkred',
                color: 'black'
            }
        }
        const classes = [];
        if (this.state.persons.length < 3){
            classes.push('red');
        }
        if (this.state.persons.length < 2){
            classes.push('bold');
        }

        return (
            <!--мы используем `StyleRoot` для того, чтобы медиа выражения вступили в силу-->
            <StyleRoot>
                <div className="App">
                    <h1>
                        Hi, I am a React-App
                    </h1>
                    <p className={classes.join(' ')}>And it's work</p>
                    <button
                        style={style}
                        onClick={this.togglePersonsHandler}>
                        Toggle Persons
                    </button>
                    {persons}
                </div>
            </StyleRoot>
        );
    }

};

export default Radium(App);
```
