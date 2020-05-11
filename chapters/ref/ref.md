## Ref

[EN]

#### Introduction

Refs allow get to access for DOM-nodes or React-elements, creating on the `render` method.

>`ref` property updating runs before calling `componentDidMount` and `componentDidUpdate` methods.

#### Working with refs

1. Using `React.createRef()`:
    * **Creating**:
    
    Refs are creating with help of `React.createRef()` and attach to React-elements using `ref` attribute. 
    Usually, refs assigned to instance class property on constructor, so on it may linking from any part of component.
    
     ```jsx
     class MyComponent extends React.Component {
       constructor(props) {
         super(props);
         this.myRef = React.createRef();
       }
       render() {
         return <div ref={this.myRef} />;
       }
     }
    ```   
   
   * **Access to refs**:
   
   When ref passing to element on the `render` method, so link on this node is access from ref's property `current`.
   
   ```jsx
    const node = this.myRef.current;
   ```
   
   >`ref` attribute doesn't using with functional components, cause for it doesn't creating instances.
                                                                                                                                                                                   
  * **Example**:
  
  ```jsx
    class CustomTextInput extends React.Component {
      constructor(props) {
        super(props);
        // создадим реф в поле `textInput` для хранения DOM-элемента
        this.textInput = React.createRef();
        this.focusTextInput = this.focusTextInput.bind(this);
      }
    
      focusTextInput() {
        // Установим фокус на текстовое поле с помощью чистого DOM API
        // Примечание: обращаемся к "current", чтобы получить DOM-узел
        this.textInput.current.focus();
      }
    
      render() {
        // описываем, что мы хотим связать реф <input>
        // с `textInput` созданным в конструкторе
        return (
          <div>
            <input
              type="text"
              ref={this.textInput} />
    
            <input
              type="button"
              value="Фокус на текстовом поле"
              onClick={this.focusTextInput}
            />
          </div>
        );
      }
    }
  ```

2. Using callback-refs
    * **Using**:
    
    Instead of passes the `ref` attribute, that creating with help of `createRef()`,
    you can passing a function. This function gets the instance of React-component or HTML DOM-element as argument, which may be saved or accessed at any other place.
    
    * **Example**:
    
    ```jsx
       class CustomTextInput extends React.Component {
         constructor(props) {
           super(props);
       
           this.textInput = null;
       
           this.setTextInputRef = element => {
             this.textInput = element;
           };
       
           this.focusTextInput = () => {
             // Устанавливаем фокус на текстовом поле ввода с помощью чистого DOM API
             if (this.textInput) this.textInput.focus();
           };
         }
       
         componentDidMount() {
           // устанавливаем фокус на input при монтировании
           this.focusTextInput();
         }
       
         render() {
           // Используем колбэк в `ref`, чтобы сохранить ссылку на DOM-элемент
           // поля текстового ввода в поле экземпляра (например, this.textInput).
           return (
             <div>
               <input
                 type="text"
                 ref={this.setTextInputRef}
               />
               <input
                 type="button"
                 value="Focus the text input"
                 onClick={this.focusTextInput}
               />
             </div>
           );
         }
       } 
    ```

[RU]

#### Введение

Рефы получают доступ к DOM-узлам или React-элементам, которые создаются в методе `render`.

>Свойство `ref` запускает обновление перед вызовом методов `componentDidMount` и `componentDidUpdate`.

#### Работа с рефами

1. Используя `React.createRef()`:
    * **Создание**:
    
    Рефы создаются с помощью `React.createRef()` и прикрепляются к React-элементам, используя атрибут `ref`. 
    Обычно, рефы присваиваются в экземпляре свойства класса в конструкторе, таким образом он может ссылаться из любой части компонента.
    
     ```jsx
     class MyComponent extends React.Component {
       constructor(props) {
         super(props);
         this.myRef = React.createRef();
       }
       render() {
         return <div ref={this.myRef} />;
       }
     }
    ```   
   
   * **Доступ к рефам**:
   
   Когда `ref` передается элементу в методе `render`, ссылка на этот узел доступна через свойство `current`.
   
   ```jsx
    const node = this.myRef.current;
   ```
   
   >Атрибут `ref` не используется с функциональными компонентами, так как для них не создаются экземпляры.                       
  
  * **Пример**:
  
  ```jsx
    class CustomTextInput extends React.Component {
      constructor(props) {
        super(props);
        // создадим реф в поле `textInput` для хранения DOM-элемента
        this.textInput = React.createRef();
        this.focusTextInput = this.focusTextInput.bind(this);
      }
    
      focusTextInput() {
        // Установим фокус на текстовое поле с помощью чистого DOM API
        // Примечание: обращаемся к "current", чтобы получить DOM-узел
        this.textInput.current.focus();
      }
    
      render() {
        // описываем, что мы хотим связать реф <input>
        // с `textInput` созданным в конструкторе
        return (
          <div>
            <input
              type="text"
              ref={this.textInput} />
    
            <input
              type="button"
              value="Фокус на текстовом поле"
              onClick={this.focusTextInput}
            />
          </div>
        );
      }
    }
  ```

2. Использование callback-refs
    * **Использование**:
    
    Вместо передачи атрибута `ref`, который создается с помощью `createRef()`,
    вы можете передать функцию. Эта функция получает экземпляр React-компонента или HTML DOM-элемента в качестве аргумента, который может быть сохранен или доступен в любом другом месте.
    
    * **Пример**:
    
    ```jsx
       class CustomTextInput extends React.Component {
         constructor(props) {
           super(props);
       
           this.textInput = null;
       
           this.setTextInputRef = element => {
             this.textInput = element;
           };
       
           this.focusTextInput = () => {
             // Устанавливаем фокус на текстовом поле ввода с помощью чистого DOM API
             if (this.textInput) this.textInput.focus();
           };
         }
       
         componentDidMount() {
           // устанавливаем фокус на input при монтировании
           this.focusTextInput();
         }
       
         render() {
           // Используем колбэк в `ref`, чтобы сохранить ссылку на DOM-элемент
           // поля текстового ввода в поле экземпляра (например, this.textInput).
           return (
             <div>
               <input
                 type="text"
                 ref={this.setTextInputRef}
               />
               <input
                 type="button"
                 value="Focus the text input"
                 onClick={this.focusTextInput}
               />
             </div>
           );
         }
       } 
    ```