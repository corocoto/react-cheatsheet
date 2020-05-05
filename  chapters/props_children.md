### `props.children`

[EN]

Every component’s `props` object has a property named `children`.

`props.children` will return everything in between a component’s opening and closing `JSX` tags.

You could write `<MyComponentClass></MyComponentClass>`, and it would still work.

Look at example below (`BigButton.js`). 

In Example 1, `<BigButton>`‘s `this.props.children` would equal the text, `“I am a child of BigButton.”`

In Example 2, `<BigButton>`‘s `this.props.children` would equal a `<LilButton />` component.

In Example 3, `<BigButton>`‘s `this.props.children` would equal `undefined`.

If a component has more than one child between its `JSX` tags, then `this.props.children` will return those children in an array. 
However, if a component has only one child, then `this.props.children` will return the single child, not wrapped in an array.

```jsx 
  import React from 'react';
  import { LilButton } from './LilButton';

  class BigButton extends React.Component {
    render() {
      console.log(this.props.children);
      return <button>Yo I am big</button>;
    }
  }


  // Example 1
  <BigButton>
    I am a child of BigButton.
  </BigButton>


  // Example 2
  <BigButton>
    <LilButton />
  </BigButton>


  // Example 3
  <BigButton />
```

[RU]

Объект `props` каждого компонента имеет свойство `children`.

`props.children` будет возвращать все, что находится между открывающим и закрывающим `JSX` тегами компонента.

Вы могли бы написать `<MyComponentClass></MyComponentClass>`, и это может заработать.

Рассмотрим пример ниже (`BigButton.js`). 

В примере 1, значение `this.props.children` компонента `<BigButton>` может быть равным следующему тексту: `“I am a child of BigButton.”`

В примере 2, значение `this.props.children` компонента `<BigButton>` может быть равным компоненту `<LilButton />`.

В примере 3, значение `this.props.children` компонента `<BigButton>` может быть равным  `undefined`.

Если компонент имеет больше, чем один дочерний элемент между `JSX` тегами, `this.props.children` будет возвращать эти дочерние элементы в виде массива. 
Однако, если компонент имеет только один дочерний элемент, `this.props.children` будет возвращать единственного ребенка, не обернутого в массив.

```jsx 
  import React from 'react';
  import { LilButton } from './LilButton';

  class BigButton extends React.Component {
    render() {
      console.log(this.props.children);
      return <button>Yo I am big</button>;
    }
  }


  // Пример 1
  <BigButton>
    I am a child of BigButton.
  </BigButton>


  // Пример 2
  <BigButton>
    <LilButton />
  </BigButton>


  // Пример 3
  <BigButton />
```
