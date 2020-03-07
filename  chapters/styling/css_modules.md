### Adding isolating styles using CSS Modules

For opportunity adding isolating styles, that will be work like native web-components styles, we are need using a force of CSS Modules.

> It be generates uniques class names on output.

**Let's get started!**

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

3. After that, we are should using next syntax for importing necessary styles:

```js
import classes from './Person.css';
```

So our CSS blocks with styles state `classes`'s properties. And we are applying our styles in the following way:

```jsx
import React from "react";
import classes from './Person.css';

const Person = (props) => {
    return (
        <div className={classes.Person}>
            <h2 onClick={props.onClick}>I'm {props.name} and I'm {props.age} years old!</h2>
            {props.children && <p>{props.children}</p>}
            <input type="text" onChange={props.onChange} value={props.name}/>
        </div>
    );
};

export default Person;
```

And it's pretty work.
