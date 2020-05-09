### Error Boundary

#### Introduction

Error boundaries are React components that catch JavaScript errors anywhere in their child component tree, log those errors, and display a fallback UI instead of the component tree that crashed. Error boundaries catch errors during rendering, in lifecycle methods, and in constructors of the whole tree below them.

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

And App component's block of code, where we are use it (error boundary component): 
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