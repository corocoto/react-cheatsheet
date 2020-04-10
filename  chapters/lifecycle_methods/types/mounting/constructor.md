## `constructor()`

React component's constructor calls before the component
will be mounting. 
Needs calling `super(props)` at the constructor beginning. IF it doesn't do, so `this.props` doesn't defined. It can be lead for bags.

Constructors on React using for 2 goals usually:
* Initialization initial state;
* Attaching event handlers for instance.

Don't use side effects or describes on a constructor. Use `componentDidMount` instead of this.