# Javascript Libraries

## AngularJS

In AngularJS, third party library get attached to the browser window object from the root app.js file. Grim but necessary

When binding variables to Angular directives, use the following bindings:

- ‘=’ for two way bindings
- ‘@’ for one way bindings
- ‘&’ for callables

If you try to use a method in an AngularJS template, AngularJS will call it constantly because it will have no way of knowing if the result of that method has changed. React does not have this issue.

## React

The componentWillReceiveProps lifecycle method on React components has been marked deprecated and can cause weird side-effects when used to synchronise state between components (which shouldn’t be done anyway because we want a single source of truth)

Using the Array.prototype.push() method on a piece of react state won’t work, and it also won’t tell you that it isn’t working, but obviously it will prevent rerendering when the state changes, even if you subsequently invoke setState()

The ‘key’ attribute and other React attributes cannot be accessed using the DOMNode.getAttribute() method

In React, when modifying a context state value via a context consumer component event handler, useRef must be used to ensure the latest state is accessible, e.g.

```(typescript)
const {notifications, setNotifications} = useContext(NotificationContext)
const notificationsRef = useRef(notifications)

const removeNotification = (key: number) => {
    setNotifications(notificationsRef.current.splice(key, 1))
}

return (<Button onClick={() => removeNotification(1)}>Dismiss</Button>)
```

If notifications was used instead of the ref it would always match the initial value it was set to in the context provider

When using a useEffect hook that call the setter returned from a useState hook or the dispatcher from useReducer, it is not necessary to pass the setter or dispatcher to useEffect as a dependency. The eslint exhausetive-deps rule should be clever enough to accept this.

### Patterns

When using an imperative API in a React component, it's good practice to wrap the API in a hook and return a ref to the API object

## Redux

The mapStateToProps method in a React component is for fetching properties out of a Redux store and mapping them to the components props
