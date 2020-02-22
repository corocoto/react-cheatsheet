### `render`
`render` is a lifecycle method!

We won’t go over render here - we’ve already talked about it plenty. However, you should understand how `render` fits into the mounting period. Whenever a component mounts, `componentWillMount` is called first, followed by `render`, followed by `componentDidMount`.

`render` belongs to two categories: 
* mounting lifecycle methods
* updating lifecycle methods. 