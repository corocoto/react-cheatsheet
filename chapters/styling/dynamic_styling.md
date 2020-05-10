## Dynamic styling (Динамическая стилизация)

[EN]

Dynamic styling very convenient. It's may using on convention blocks, when we are want to change button's `background-color` styling property, as example. 
Namely, when we are clicking on it.

Let's look on a solution of this task:

```jsx
import React, {Component} from 'react';
import './App.css';
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
            borderRadius: '4px'
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
        }
        return (
            <div className="App">
                <h1>
                    Hi, I am a React-App
                </h1>
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

export default App;
```


[RU]

Динамическая стилизация очень удобна. Она может быть использована в условных блоках, например, когда мы хотим изменить занчение свойства `background-color` у кнопки.
 
А именно, когда мы нажимаем на неё.

Давайте посмотрим на решение этой задачи:

```jsx
import React, {Component} from 'react';
import './App.css';
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
            borderRadius: '4px'
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
        }
        return (
            <div className="App">
                <h1>
                    Hi, I am a React-App
                </h1>
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

export default App;
```