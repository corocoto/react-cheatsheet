## Redirect

[EN]

### Description

**Redirect** component using for redirecting from one location to another.

### Available properties

* **to: string**
    The URL to redirect to. You can also to pass necessary params into this string.
    
    **Example**:
    
    ```jsx
      <Redirect to="/somewhere/else" />
    ```

* **to: object**
    A location to redirect to. All necessary params are pass into object.
    
   **Example**:
   
  ```jsx
      const data = { 
          pathname: "/login",
          search: "?utm=your+face",
          state: {referrer: currentLocation} 
      };
      ...
      <Redirect to={data}/>
   ```         

* **from: string**

    A pathname to redirect from.

    **Example**:
    
    ```jsx
    <Redirect from="/404page" to="/" />
    ``` 

* **exact: boolean**

    Equivalent to **Route.exact**.
    
    **Example**:
    
    ```jsx
    <Redirect from="/404page" to="/" exact />  
    ```

[RU]

### Описание

Компонент **Redirect** используется для перенавления с одной локации на другую.

### Доступные свойства

* **to: string**
    URL, куда будет происходить перенаправление. Вы также можете передавать наобходимые параметры в эту строку.
    
    **Пример**:
    
    ```jsx
      <Redirect to="/somewhere/else" />
    ```

* **to: object**
    Локация, куда будет происходить перенаправление. Все необходимые параметры пережаются в объект.
    
   **Пример**:
   
  ```jsx
      <Redirect
        to={{
          pathname: "/login",
          search: "?utm=your+face",
        }}
      />
   ```

* **from: string**

    Путь откуда будет происходить пернаправление.

    **Пример**:
    
    ```jsx
    <Redirect from="/404page" to="/">
    ```   
  
* **exact: boolean**

    Эквивалентно **Route.exact**.
    
    **Пример**:
    
    ```jsx
    <Redirect from="/404page" to="/" exact />  
    ```    