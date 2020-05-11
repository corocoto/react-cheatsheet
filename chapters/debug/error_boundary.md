## Error Boundary

[EN]

#### Introduction

Error boundaries are React components that catch JavaScript errors anywhere in their child components tree, log those errors, and display a fallback UI instead of the component tree that crashed. Error boundaries catch errors during rendering, in lifecycle methods, and in constructors of the whole tree below them.

#### Creating Error Boundary component

```jsx
import React, {Component} from "react";

export class ErrorBoundary extends Component{
    constructor(props) {
        super(props);
        this.state = {
            hasError: false,
            errorMessage: ''
        }
    }

    componentDidCatch(error, errorInfo) {
        this.setState({
            hasError: true,
            errorMessage: error
        })
    }

    render() {
        if (this.state.hasError){
            return <h1>{this.state.errorMessage}</h1>
        }else{
            return this.props.children;
        }
    }
}
```

And **App** component's block of code where we are use it (**error boundary** component): 

```jsx
render() {
    let persons = null;
    if (this.state.showPersons) {
        persons = (
            <div>
                {this.state.persons.map((person, index) => {
                    return <ErrorBoundary key={person.id}>
                        <Person
                            name={person.name}
                            age={person.age}
                            onClick={index => this.deleteEventHandler(index)}
                            onChange={event => this.changeEventHandler(event, person.id)}/>
                    </ErrorBoundary>
                    }
                )}
            </div>
        );
    }
    const assignClasses = [];
    if (this.state.persons.length < 3) {
        assignClasses.push(classes.red);
    }
    if (this.state.persons.length < 2) {
        assignClasses.push(classes.bold);
    }

    return (
        <div className={classes.App}>
            <h1>Hi, I am a React-App</h1>
            <p className={assignClasses.join(' ')}>And it's work</p>
            <button
                className={classes.button}
                alt={this.state.showPersons ? 'show' : undefined}
                onClick={this.togglePersonsHandler}>
                Toggle Persons
            </button>
            {persons}
        </div>
    ;
}
```

[RU]

#### Введение

Error boundaries - это React компонеты, которые ловят JavaScript ошибки  где-нибудь в их дереве дочерних компонентов, логируют эти оишбки, и отображают резервный интерфейс вместо дерева компонента, который сломан. Error boundaries ловят ошибки через отрисовку, в методах жизненного цикла, и в конструкторах всего его внутреннего дерева.

#### Создание компонента Error Boundary

```jsx
import React, {Component} from 'react';

export class ErrorBoundary extends Component{
    constructor(props) {
        super(props);
        this.state = {
            hasError: false,
            errorMessage: ''
        }
    }

    componentDidCatch(error, errorInfo) {
        this.setState({
            hasError: true,
            errorMessage: error
        })
    }

    render() {
        if (this.state.hasError){
            return <h1>{this.state.errorMessage}</h1>
        }else{
            return this.props.children;
        }
    }
}
```

И блок кода компонента **App**, где мы используем его (компонент **error boundary**): 

```jsx
render() {
    let persons = null;
    if (this.state.showPersons) {
        persons = (
            <div>
                {this.state.persons.map((person, index) => {
                    return <ErrorBoundary key={person.id}>
                        <Person
                            name={person.name}
                            age={person.age}
                            onClick={index => this.deleteEventHandler(index)}
                            onChange={event => this.changeEventHandler(event, person.id)}/>
                    </ErrorBoundary>
                    }
                )}
            </div>
        );
    }
    const assignClasses = [];
    if (this.state.persons.length < 3) {
        assignClasses.push(classes.red);
    }
    if (this.state.persons.length < 2) {
        assignClasses.push(classes.bold);
    }

    return (
        <div className={classes.App}>
            <h1>Hi, I am a React-App</h1>
            <p className={assignClasses.join(' ')}>And it's work</p>
            <button
                className={classes.button}
                alt={this.state.showPersons ? 'show' : undefined}
                onClick={this.togglePersonsHandler}>
                Toggle Persons
            </button>
            {persons}
        </div>
    ;
}
```