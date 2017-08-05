###### Running the starter project
```
$ npm install
$ npm start
```

###### Installing new modules
```
$ npm install --save axios redux-promise
```

##### React Redux Workflow
First, create the action creator.
Secondly, create the reducer to watch for the action.
Lastly, wire up the action creator to the component with the connect helper.

ACTION CREATOR > REDUCER > COMPONENT

###### Grepping across all of your React projects
```
grep -R 'Loading' * --exclude-dir node_modules
grep -R 'axios' * --exclude-dir node_modules --exclude *.json
```

###### REPL tool
https://stephengrider.github.io/JSPlaygrounds/

JSPlaygrounds ships with lodash by default. If you want to import more libraries,
you can clone your forked JSPlaygrounds repo in GitHub and modify.

In JSPlaygrounds, you can run any JS code...
```
const posts = [
  {"id": 1, "name": "rusty", "age": 10},
  {"id": 2, "name": "grizzly", "age": 12},
  {"id": 3, "name": "cloudy", "age": 14}
]

_.mapKeys(posts, 'id');
```
