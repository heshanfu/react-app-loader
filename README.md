# react-app-loader
Production ready library for handling Microfrontends, written in React.

## [Demo](https://entria.github.io/react-app-loader/)

## How to use

### Create a config file for each external app:
```
$ touch AnyExternalApp.js
```

### Then, wrap it with `withAppLoader` [HOC](https://reactjs.org/docs/higher-order-components.html):
```jsx
// @flow

import withAppLoader from '@entria/react-app-loader';

const elementId = 'github';
const appUrl = 'https://github.com/';

const AppLoader = withAppLoader({ elementId, appUrl });

export default AppLoader;

```

#### Or you can try a more complex way, passing some `props`:
```jsx
// @flow

import React from 'react';
import withAppLoader from '@entria/react-app-loader';

const elementId = 'github';
const appUrl = 'https://github.com/';

type Props = {
  externalUrl: string,
};

const AnyExternalApp = (props: Props) => {
  const { externalUrl } = props;
  const AppLoader = withAppLoader({
    elementId,
    appUrl: externalUrl != null && externalUrl.length > 0 ? externalUrl : appUrl
  });
  return <AppLoader />;
};

export default AnyExternalApp;

```

### Import it on your React app:
```jsx
import React, { Component } from 'react';
import logo from './logo.svg';
import './App.css';

import AnyExternalApp from './AnyExternalApp';

class App extends Component {
  render() {
    return (
      <div className="App">
        <AnyExternalApp />
      </div>
    );
  }
}

export default App;
```

### Import `babel-polyfill` on your `index.js`
```jsx
import 'babel-polyfill';
```

### Run \o/

## [Example](https://github.com/jgcmarins/react-app-loader/tree/master/example/my-awesome-app)

## TODO
- [ ] Add a working example with [React Router](https://github.com/ReactTraining/react-router)
- [ ] Add an example with Loading Component
- [ ] Add an example with shared authentication layer
- [ ] Add an example with shared style
- [ ] Add an example with more complex `props` and `state`
- [ ] More informaton about development setup (handling cors, etc)
- [ ] Relay?
- [ ] Redux?
