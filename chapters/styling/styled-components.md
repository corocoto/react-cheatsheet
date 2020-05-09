### `styled-components` library

[`styled-components`](https://styled-components.com/) lets you write actual CSS in your JavaScript. This means you can use all the features of CSS you use and love, including media queries, all pseudo-selectors, nesting, etc.

For using it, we are need install this package:

```bash
    $ npm i styled-components --save
```

After that, you are need importing this package:

```jsx
    import styled from 'styled-components';
```

Good! After that, we can create our style components on this file.

Let's look, how doing it:

```jsx
const Person = (props) => {
    const StyledDiv = styled.div`
        width: 60%;
        border: 1px solid #eee;
        box-shadow:  0 2px 3px 0 #ccc;
        padding: 16px;
        text-align: center;
        margin: 14px auto;
        /*set media queries*/
        @media (min-width : 500px) {
            width: 400px
        }
    `;

    return (
        <StyledDiv>
            <h2 onClick={props.onClick}>I'm {props.name} and I'm {props.age} years old!</h2>
            {props.children && <p>{props.children}</p>}
            <input type="text" onChange={props.onChange} value={props.name}/>
        </StyledDiv>);
};
```

In the example above we creating new styled component named as `StyledDiv`.
For creating we are call next function: `styled.div`.

After this structure, we are use target template literal (<code>``</code>). Into this template, we are setting our styles (write as regular CSS).

### Changing styles based on attribute value

For understand how it doing, let's look an example bellow:

```jsx
const StyledButton = styled.button`
    background-color: ${props=> props.alt ? 'red' : 'green'};
    color: white;
    font: inherit;
    padding: 8px;
    border: 1px solid blue;
    borderRadius: 4px;
    /*set hover effect*/
    &:hover {
        background-color: ${props => props.alt ? 'salmon' : 'lightgreen'};
        color: black;
    }
`;

...
render(){
    ...
    return (
        <div className="App">
            <h1>Hi, I am a React-App</h1>
            <p className={classes.join(' ')}>And it's work</p>
            <StyledButton
                alt={this.state.showPersons}
                onClick={this.togglePersonsHandler}>
                Toggle Persons
            </StyledButton>
            {persons}
        </div>
    );
}
```