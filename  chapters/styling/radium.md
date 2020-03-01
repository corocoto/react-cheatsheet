### Using pseudo classes, pseudo elements and media queries in inline styles

For possibility to adding and using pseudo classes, pseudo elements or maybe media queries, you are need install [radium](https://www.npmjs.com/package/radium) package, which allows doing it.

For install this package, you are need using next command:

```bash
$ npm install radium
```

After that, we are necessary importing this package on that file, on which we are want to add pseudo classes, pseudo elements or media queries. As example, it file is `App.js`:

```jsx
import React, {Component} from 'react';
import './App.css';
import Radium from "radium";
import Person from './Person/Person';
```

At the end this file (when we are exporting component), we are need  wrap `App` component into `Radium`:

```jsx
export default Radium(App);
```

Next step is adding styles. Let's look on a part of App component's  code: 

```jsx
import React, {Component} from 'react';
import './App.css';
import Radium from "radium";
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
            /*the ability to write such syntax is provided by the radium package*/
            /*in this case, we are add styles for hover effect*/
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

For writing media queries using `radium` package. You are need to write syntax, as next:
```jsx
const style = {
    '@media (min-width : 500px)': {
        width: '400px'
    }
};
```

Let's look how add media queries for `Person` component:

```jsx
import React from "react";
import Radium from "radium";
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

If we are using media queries, so we must be loading `StyleRoot`.
Let's add it into `App.js` file. And wrap our html structure into it:

```jsx
import React, {Component} from 'react';
import './App.css';
import Radium, {StyleRoot} from "radium";
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
