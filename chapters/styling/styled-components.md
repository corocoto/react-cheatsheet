## styled-components library (Библиотека styled-components)

[EN]

[`styled-components`](https://styled-components.com/) lets to you write actual CSS in your JavaScript. It means that you can use all the features of CSS, that you use and love, including media queries, all pseudo-selectors, nesting, etc.

For using it, we are need to install this package:

```bash
    $ npm i styled-components --save
```

After that, you are need to importing this package:

```jsx
    import styled from 'styled-components';
```

Good! After that, we can create our style components on this file.

Let's take a look, how we can doing it:

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

In example above we creating new styled component named as **StyledDiv**.
 We're call `styled.div` function for it creating.

After this structure, we are use a target template literal (<code>``</code>). Into this template we are setting our styles (it writes as regular CSS).

### Changing styles based on attribute value

For understand how doing it, let's take a look into example bellow:

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

[RU]

[`styled-components`](https://styled-components.com/) дает вам возможность написания действующего CSS внутри вашего JavaScript. Это подразумевает то, что вы можете использовать все особенности CSS, которые вы используете и любите, включая медиа выражения, всевозможные псевдоселекторы, вложенность и т.д.

Для его использования нам нужно установить пакет:

```bash
    $ npm i styled-components --save
```

После этого, вам нужно его импортировать:

```jsx
    import styled from 'styled-components';
```

Хорошо! Далее, мы можем создавать наши styled-компоненты в этом файле.

Давайте посмотрим на то, как мы можем сделать это:

```jsx
const Person = (props) => {
    const StyledDiv = styled.div`
        width: 60%;
        border: 1px solid #eee;
        box-shadow: 0 2px 3px 0 #ccc;
        padding: 16px;
        text-align: center;
        margin: 14px auto;

        /* установка медиа выражений */
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

В примере выше, мы создали новый styled-компонент, названный как **StyledDiv**.
Мы вызываем функцию `styled.div` для его создания.

После этой структуры, мы используем целевой шаблонный литерал(<code>``</code>). Внутри этого шаблона мы устанавливаем наши стили (они пишутся, как обычный CSS).

### Изменение стилей исходя из значения атрибута

Для понимания того, как это делать, давайте рассмотрим пример ниже:

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