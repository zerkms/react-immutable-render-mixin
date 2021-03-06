react-immutable-render-mixin
============================

This library exposes 3 distict options for immutable rendering:

* Mixin for `React.createClass` support
* HoC ( _decorator_ ) for `React.Component`
* shallowEqualImmutable function to allow custom `shouldComponentUpdate` implementations

This library when used as a mixin/decorator replaces the [PureRenderMixin](http://facebook.github.io/react/docs/pure-render-mixin.html) when using [facebook/immutable-js](https://github.com/facebook/immutable-js) library with [React](https://github.com/facebook/react)

This Mixin and HoC implements `shouldComponentUpdate` method using prop and state equality with Immutable.is().

We also expose the `shallowEqualImmutable` to allow developers to craft a custom `shouldComponentUpdate` method as needed.

Installation
------------

```sh
npm i react-immutable-render-mixin
```

Usage as Mixin
-----

```js
import immutableRenderMixin from 'react-immutable-render-mixin';

React.createClass({
  mixins: [immutableRenderMixin],

  render: function() {
    return <div className={this.props.className}>foo</div>;
  }
});
```

Usage as a HoC
-----

```js
import React from 'react';
import { immutableRenderDecorator } from 'react-immutable-render-mixin';

class Test extends React.Component {
  render() {
    return <div></div>;
  }
}

export default immutableRenderDecorator(Test);
```

Usage as Decorator
-----

```js
import React from 'react';
import { immutableRenderDecorator } from 'react-immutable-render-mixin';

@immutableRenderDecorator
class Test extends React.Component {
  render() {
    return <div></div>;
  }
}
```

Usage with a custom `shouldComponentUpdate`
-----

```js
import React from 'react';
import { shallowEqualImmutable } from 'react-immutable-render-mixin';

class Test extends React.Component {
  shouldComponentUpdate(nextProps, nextState) {
    return !shallowEqualImmutable(this.props, nextProps) || !shallowEqualImmutable(this.state, nextState);  
  }

  render() {
    return <div></div>;
  }
}
```

Usage with <= ES5
-----

Exports:

```js
var immutableRenderMixin = require('react-immutable-render-mixin').default;

var immutableRenderDecorator = require('react-immutable-render-mixin').immutableRenderDecorator;

var shallowEqualImmutable = require('react-immutable-render-mixin').shallowEqualImmutable;
```

Full Example:

```js
var immutableRenderMixin = require('react-immutable-render-mixin').default;

React.createClass({
  mixins: [immutableRenderMixin],

  render: function() {
    return <div className={this.props.className}>foo</div>;
  }
});
```
