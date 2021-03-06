### Running the starter project
```
$ npm install
$ npm start
```

### Installing new modules
```
$ npm install --save axios redux-promise
```

### Renaming stuff
Use vim
```
%s/POST/LINK/gec | %s/Post/Link/gec | %s/post/link/gec
```

### React Redux Workflow
First, create the action creator.
Secondly, create the reducer to watch for the action.
Lastly, wire up the action creator to the component with the connect helper.

ACTION CREATOR > REDUCER > COMPONENT

### Other React and Redux libraries
There's lots of great source code to read in the projects below...

[react-router](https://reacttraining.com/react-router/web/guides/philosophy) (github link [here](https://github.com/ReactTraining/react-router)) has many routers, but I'll mostly be using [react-router-dom](https://github.com/ReactTraining/react-router/tree/master/packages/react-router-dom) . I don't think I need to use [react-router-redux](https://github.com/reactjs/react-router-redux) at all.

[redux-form](https://github.com/erikras/redux-form) works with React Redux to enable an html form in React to use Redux to store all of its state.



[redux-thunk](https://github.com/gaearon/redux-thunk) is middleware allows you to write action creators that return a function instead of an action. The thunk can be used to delay the dispatch of an action, or to dispatch only if a certain condition is met. The inner function receives the store methods dispatch and getState as parameters.

[Reselect](https://github.com/reactjs/reselect) allows you to re-use existing redux state to create derived, computed state. It elimitates duplication of state in redundant components, allowing you to use minimal redux states. For example, you can track changes in 'selectItems' state and 'AllItems' state. If the 'selectedItems' state changes, reselect will automatically calcuate derived state and give you a result. It also helps with caching and performances. you can call selectors as regular functions inside mapStateToProps().

[Normalizr](https://github.com/paularmstrong/normalizr) helps you transform complex API response object into more compact JSON.

[Redux Logger](https://github.com/evgenyrodionov/redux-logger) is middleware that automatically logs previous state, action, new state and errors on each reducer call.

[Redux Devtool](https://github.com/gaearon/redux-devtools) lets you inspect every state and action payload. It also lets you go back in time by “cancelling” actions.

[And many more ...](https://github.com/enaqx/awesome-react#redux-general-resources).

#### Grepping across all of your React projects
```
grep -R 'Loading' * --exclude-dir node_modules
grep -R 'axios' * --exclude-dir node_modules --exclude *.json
```

### REPL tool
[JSPlaygrounds](https://stephengrider.github.io/JSPlaygrounds)

JSPlaygrounds ships with lodash by default. If you want to import more libraries,
you can clone your forked JSPlaygrounds repo in GitHub and modify.

### React notes
Component state should not be changed in render methods. Render should be idempotent and pure.
You can initialize this.state via assignment operator in your constructor with an object. 
Any other method (lifecycle or custom) except for render use this.setStre({key: value}).
You only need a constructor if your component reqires its own state OR you need to use this.method = this.method.bind(this). 
Within a component, you are free to store additional fields directly on 'this' as long at the field
has nothing to do with anything visual. For example, a timer instance can be stored as this.timer within
componentDidMount. Teardown the timer in componentWillUnmount. If you dont use something in render(), it shouldn't be in state.

React may batch multiple setState() calls into a single update for performance.
Because this.props and this.state may be updated asynchronously, you should not rely on their values for calculating the next state. For example, this code may fail to update the counter:

 ```
// Wrong
this.setState({
  counter: this.state.counter + this.props.increment,
});
```

To fix it, use a second form of setState() that accepts a function rather than an object. That function will receive the previous state as the first argument, and the props at the time the update is applied as the second argument:

```
// Correct
this.setState((prevState, props) => ({
  counter: prevState.counter + props.increment
}));
```

