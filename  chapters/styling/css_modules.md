### Adding isolating styles using CSS Modules

With CSS modules, you can write normal CSS code and make sure, that it only applies to a given component.

It's not using magic for that, instead it'll simply automatically generate unique CSS class names for you. And by importing a JS object and assigning classes from there, you use these dynamically generated, unique names. So the imported JS object simply exposes some properties which hold the generated CSS class names as values.

**Let's doing it!**

1. First, that we will doing - are run next command:

```bash
$ npm run eject
```

So, after that, we'll get the `config` folder, that we also can change. Also we are getting the `scripts` folder, but now we are need the `config` folder only.


2. Second, we'll modifying the webpack config a little bit more. 

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

3. In `Post.module.css `file writes something like this:
```css
.Post {
    color: red;
}
```

And in `Post Component` file writes next code:
```jsx
import classes from './Post.module.css';
 
const post = () => (
    <div className={classes.Post}>...</div>
);
```

Here, `classes.Post`  refers to an automatically generated `Post` property on the imported classes  object. That property will in the end simply hold a value like `Post__Post__ah5_1`.

So your `.Post` class was automatically transformed to a different class (`Post__Post__ah5_1`) which is unique across the application. 
You also can't use it accidentally in other components, because you don't know the generated string! You can only access it through the classes object. And if you import the CSS file (in the same way) in another component, the classes  object there will hold a `Post` property which yields a different (!) CSS class name. Hence it's scoped to a given component.

By the way, if you somehow also want to define a `global` (i.e. un-transformed) CSS class in such a `.css` file, you can prefix the selector with `:global`.

Example for this case:

```css
:global .Post { ... } 
```

Now you can use `className="Post"` anywhere in your app and receive that styling.
