## Context (Контекст)

[EN]

### Introduction 

**Context** provides a way to pass data through the component tree without having to pass props down manually at every level.

In a typical React application, data is passing top-down (parent to child) via `props`, but this can be cumbersome for certain types of `props` (e.g. locale preference, UI theme) that are required by many components within an application. **Context** provides a way to share values like these between components without having to explicitly pass a prop through every level of the tree.

### When to Use Context

**Context** is designed to share data that can be considered **global** for a tree of React components, such as the current authenticated user, theme, or preferred language. For example, in the code below we manually thread through a **theme** prop in order to style the **Button** component:

```jsx
class App extends React.Component {
  render() {
    return <Toolbar theme="dark" />;
  }
}

function Toolbar(props) {
  // Компонент Toolbar должен передать проп "theme" ниже,
  // фактически не используя его. Учитывая, что у вас в приложении
  // могут быть десятки компонентов, использующих UI-тему,
  // вам придётся передавать проп "theme" через все компоненты.
  // И в какой-то момент это станет большой проблемой.
  return (
    <div>
      <ThemedButton theme={props.theme} />
    </div>
  );
}

class ThemedButton extends React.Component {
  render() {
    return <Button theme={this.props.theme} />;
  }
}
```

Using context, we can avoid passing props through intermediate elements:

```jsx
// Контекст позволяет передавать значение глубоко
// в дерево компонентов без явной передачи пропсов
// на каждом уровне. Создадим контекст для текущей
// UI-темы (со значением "light" по умолчанию).
const ThemeContext = React.createContext('light');

class App extends React.Component {
  render() {
    // Компонент Provider используется для передачи текущей
    // UI-темы вниз по дереву. Любой компонент может использовать
    // этот контекст и не важно, как глубоко он находится.
    // В этом примере мы передаём "dark" в качестве значения контекста.
    return (
      <ThemeContext.Provider value="dark">
        <Toolbar />
      </ThemeContext.Provider>
    );
  }
}

// Компонент, который находится в середине,
// теперь не должен явно передавать UI-тему вниз.
function Toolbar(props) {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

class ThemedButton extends React.Component {
  // Определяем contextType, чтобы получить значение контекста.
  // React найдёт (выше по дереву) ближайший Provider-компонент,
  // предоставляющий этот контекст, и использует его значение.
  // В этом примере значение UI-темы будет "dark".
  static contextType = ThemeContext;
  render() {
    return <Button theme={this.context} />;
  }
}
```

### API

* **`React.createContext`**
    
    ```jsx
    const MyContext = React.createContext(defaultValue);
    ```
  
  Creates a **Context** object. When React renders a component that subscribes to this **Context** object it will read the current context value from the closest matching **Provider** above it in the tree.
  
  The `defaultValue` argument is only used when a component doesn't have a matching `Provider` above it in the tree. This can be helpful for testing components in isolation without wrapping them. 
  
  >**Note:** passing `undefined` as a `Provider` value does not cause consuming components to use `defaultValue`.

[RU]

### Введение 

**Контекст** предоставляет путь пердачи данных через дерево компонента без наличия передчи `props` вручную вниз на каждом уровне.

В типчном React приложении, данные передаются сверху вниз (от родителя к ребенку) через `props`, но здесь могут быть некоторые громозкие типы `props`'ов (н-р, предпочтение локали, UI тема), которые запривались многими компонентами в приложении. **Context** предоставляет путь передачи значений между компонентами без возможности явной передачи пропа через каждый уровень дерева.

### Когда использовать Контекст

**Контекст** спроектирован для возможности передачи данных, которые могут считаться **глобальными** для дерева React компонентов, таких как, текущий авторизованный пользователь, тема, или предпочтение локали. Для примера, в коде ниже мы вручную передаем данные через проп **theme** по порядку для стилизации компонента **Button**:

```jsx
class App extends React.Component {
  render() {
    return <Toolbar theme="dark" />;
  }
}

function Toolbar(props) {
  // Компонент Toolbar должен передать проп "theme" ниже,
  // фактически не используя его. Учитывая, что у вас в приложении
  // могут быть десятки компонентов, использующих UI-тему,
  // вам придётся передавать проп "theme" через все компоненты.
  // И в какой-то момент это станет большой проблемой.
  return (
    <div>
      <ThemedButton theme={props.theme} />
    </div>
  );
}

class ThemedButton extends React.Component {
  render() {
    return <Button theme={this.props.theme} />;
  }
}
```

Используя **контекст**, мы можем избежать предачи `props` через промжуточное кол-во элементов:

```jsx
// Контекст позволяет передавать значение глубоко
// в дерево компонентов без явной передачи пропсов
// на каждом уровне. Создадим контекст для текущей
// UI-темы (со значением "light" по умолчанию).
const ThemeContext = React.createContext('light');

class App extends React.Component {
  render() {
    // Компонент Provider используется для передачи текущей
    // UI-темы вниз по дереву. Любой компонент может использовать
    // этот контекст и не важно, как глубоко он находится.
    // В этом примере мы передаём "dark" в качестве значения контекста.
    return (
      <ThemeContext.Provider value="dark">
        <Toolbar />
      </ThemeContext.Provider>
    );
  }
}

// Компонент, который находится в середине,
// теперь не должен явно передавать UI-тему вниз.
function Toolbar(props) {
  return (
    <div>
      <ThemedButton />
    </div>
  );
}

class ThemedButton extends React.Component {
  // Определяем contextType, чтобы получить значение контекста.
  // React найдёт (выше по дереву) ближайший Provider-компонент,
  // предоставляющий этот контекст, и использует его значение.
  // В этом примере значение UI-темы будет "dark".
  static contextType = ThemeContext;
  render() {
    return <Button theme={this.context} />;
  }
}
```

### API

* **`React.createContext`**
    
    ```jsx
    const MyContext = React.createContext(defaultValue);
    ```
  
  Создание объекта **Context**. Когда React отрисовывает компонент, который подписан на этот объект **Context**, он будет читать текущее значение контекста исходя из ближайшего соответствия  **Provider**, который находится выше в дереве.
  
 Аргумент `defaultValue` используется только, когда компонент не находит соотвествия с **Provider**, находящийся выше в дереве. Это может помочь при тестировании компонентов, находящихся в изоляции, без необходимости их оборачнивания. 
  
 >**Примечание:** передача `undefined` в качестве значения **Provider** не приводит к тому, что потребляющие компоненты используют `defaultValue`.