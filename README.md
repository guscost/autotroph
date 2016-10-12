# simple-flux
A simple Flux implementation without any build requirements or dependencies. This is easier to learn, but for real projects you should consider [Redux](http://redux.js.org/) instead!

## Getting Started
This library is just an `sf` module with two properties: `dispatcher` is based on the [Flux reference dispatcher](https://github.com/facebook/flux/blob/master/src/Dispatcher.js), and `createStore` is a helper function for creating simple stores that work with this dispatcher.

## Stores
The output of a call to `sf.createStore()` is an object that has `.subscribe()`, `.unsubscribe()`, and `.getState()` functions. Subscribe your render function to these stores, and then pass your action objects to `sf.dispatcher.dispatch()`.

## initialState
The first argument to `sf.createStore()` is an object with the initial values of your state variables. This object will be passed into the `actionHandler` along with every `action` that is dispatched. By default changes are saved by mutating this object, and you are responsible for adding any immutable behavior. You can assign immutable references to any property on `initialState`, or make `initialState` an array of historical state objects.

## actionHandler
The second argument to `sf.createStore()` is a function that takes the current state and the action object as arguments, and returns `true` if the app should re-render. Check the action and either update the state or make a new immutable version in this handler. In most cases this function will return `true`, but you can return `false` to skip re-rendering.

## Example
See [test.html](https://github.com/guscost/simple-flux/blob/master/test.html) for a usage example. This file can be downloaded and run locally in most browsers with no setup.
