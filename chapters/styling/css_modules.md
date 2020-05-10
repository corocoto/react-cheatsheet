## Adding isolating styles using CSS Modules (Добавление изолирующих стилей, используя CSS Modules)

[EN]

With CSS modules you can write normal CSS code and make sure, that it only applies to a given component.

It's not using magic for that, instead it'll simply automatically generate unique CSS class names for you. And by importing a JS object and assigning classes from there you use these dynamically generated unique names. So the imported JS object simply exposes some properties which hold the generated CSS class names as values.

**Let's take a look how it works!**

1. First, that we will be doing - run next command:

```bash
$ npm run eject
```

So, after that, we'll get the **config** folder, that we also can change. Wwe are also getting the **scripts** folder, but now we are need the **config** folder only.

2. Second, we'll be modifying the *webpack config* a little bit more. 

It's named be like the `webpack.config.js`. Open it and find the string, that beginning like that:
    * `test: cssRegex` (in my case)
    * `test: /\.css$/`
    
After we found this block of code. We'll modify this object, so it'll be look like that:

````js
{
    test: cssRegex,
    exclude: cssModuleRegex,
    use: getStyleLoaders({
        importLoaders: 1,
        modules: {
            localIdentName: "[name]__[local]___[hash:base64:5]",
        },
        sourceMap: isEnvProduction && shouldUseSourceMap,
    ),
    sideEffects: true,
}
````

3. In `Post.module.css` file writes something like this:

```css
.Post {
    color: red;
}
```

And in **Post** component file writes next code:

```jsx
import classes from './Post.module.css';
 
const post = () => (
    <div className={classes.Post}>...</div>
);
```

Here, `classes.Post` refers to an automatically generated `Post` property on the imported classes  object. That property will in the end simply hold a value like `Post__Post__ah5_1`.

So your `.Post` class was automatically transformed to a different class (`Post__Post__ah5_1`) which is unique across the application. 
You also can't use it accidentally in other components, because you don't know the generated string! You can only access it through the classes object. And if you import the CSS file (in the same way) in another component, the classes  object there will hold a `Post` property which yields a different (!) CSS class name. Hence, it's scoped to a given component.

By the way, if you somehow also want to define a  **global** (i.e. un-transformed) CSS class in such a `.css` file, you can prefix the selector with `:global`.

Example for this case:

```css
:global .Post { ... } 
```

Now you can use `className="Post"` anywhere in your app and receive that styling.


### Some cool features

* **The `composes` keyword**

Let’s imagine, that we have a module called `type.css` for our text styles. In that file we might have the following:

```css
.serif-font {
  font-family: Georgia, serif;
}

.display {
  composes: serif-font;
  font-size: 30px;
  line-height: 35px;
}
```

We would declare one of those classes in our template like so:

```jsx
import type from "./type.css";

element.innerHTML = 
  `<h1 class="${type.display}">
    This is a heading
  </h1>`;
```

This would result in markup like:

```html
<h1 class="_type__display_0980340 _type__serif_404840">
  Heading title
</h1>
```

> Both classes have been bound to the element by the use of the `composes` keyword

So we can even compose it from a specific class in a separate CSS file:

```css   
.element {
    composes: dark-red from "./colors.css";
    font-size: 30px;
    line-height: 1.2;
}
```

[RU]

C CSS модулями вы можете писать нормальный CSS код и быть уврененным в том, что он относится только к данному компоненту.

Он не использует магию для этого, вместо этого он просто будет автоматически генерировать уникальные имена CSS классов для вас. И импортируя JS-объект, и назначая классы туда, вы используете эти динамически сгенерированные уникальные имена. Пэтому импортированный JS-объект просто выставляет некоторые свойства, которые содержат сгенерированные имена CSS-классов в качестве значений.

**Давайте посмотрим, как это работает!**

1. Первое, что мы сделаем - запустим следующую команду:

```bash
$ npm run eject
```

Так что, после этого, мы получим папку `config`, которую мы также можем изменить. Также мы получаем папку `scripts`, но сейчас нам нужна только папка `config`.


2. Второе, мы немного изменим конфиг webpack. 

Он назван, как `webpack.config.js`. Откроем его и найдем строку, которая начниается так:
    * `test: cssRegex` (в моем случае)
    * `test: /\.css$/`
    
После того, как мы нашли этот блок кода, мы изменим этот объект таким образом, что он будет выглядеть так:

````js
{
    test: cssRegex,
    exclude: cssModuleRegex,
    use: getStyleLoaders({
        importLoaders: 1,
        modules: {
            localIdentName: "[name]__[local]___[hash:base64:5]",
        },
        sourceMap: isEnvProduction && shouldUseSourceMap,
    ),
    sideEffects: true,
}
````

3. В `Post.module.css ` файле напишем что-то похожее на это:
```css
.Post {
    color: red;
}
```

И в компоненте **Post**  напишем следующий код:

```jsx
import classes from './Post.module.css';
 
const post = () => (
    <div className={classes.Post}>...</div>
);
```

Здесь `classes.Post` ссылается на автоматически сгенерированное свойство `Post` в импортируемом объекте `classes`. Это свойство в конечном итоге будет содержать значение похожее на `Post__Post__ah5_1`.

Таким образом, ваш класс `.Post`  был автоматически трансофрмирован в другой класс (`Post__Post__ah5_1`), который является уникальным для всего приложения. Вы также не можете использовать его случайно в других компонентах, так как вы не знаете вид сгенерированной строки! Вы моежте только получить доступ к ней через объект `classes`. И если вы импортируете CSS-файл (с тем же расположением) в другом компоненте, объект `classes` здесь будет содержать свойство `Post`, которое предоставляет другое (!) имя CSS класса. Следовательно, он будет находиться в области видимости полученного компонента.

Кстати, если вы как-то хотите определить **глобальную область видимости** (т.е не трасформируемую) для CSS класса в том же `.css` файле, вы можете добавить префикс `:global` перед селктором.

Пример для этого случая:

```css
:global .Post { ... } 
```

Сейчас вы можете использовать `className="Post"` в любом месте вашего приложения и получить эту стилизацию.


### Некоторые крутые фичи

* **Ключевое слово `composes`**

Давайте представим, что у нас есть модуль, названный `type.css`, для стилизации нашего текста. В этом файле мы можем иметь следующее:

```css
.serif-font {
  font-family: Georgia, serif;
}

.display {
  composes: serif-font;
  font-size: 30px;
  line-height: 35px;
}
```

Мы можем объявлять один из этих классов в нашем шаблоне, как показанно здесь:

```jsx
import type from './type.css';

element.innerHTML = 
  `<h1 class="${type.display}">
    This is a heading
  </h1>`;
```

Это приведет к следующей разметке:

```html
<h1 class="_type__display_0980340 _type__serif_404840">
  Heading title
</h1>
```

> Оба класса были прикреплены к элементу благодаря использованию ключевого слова `composes`.

Таким образом, мы даже можем создавать конструкции, брав класс из отдельного CSS-файла.

```css   
.element {
    composes: dark-red from './colors.css';
    font-size: 30px;
    line-height: 1.2;
}