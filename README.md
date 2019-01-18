![CF](http://i.imgur.com/7v5ASc8.png) LAB
=================================================

## Lab 37 < Auth /> and <Login /> with React Context

### Author: Kevin O'Halloran

### Links and Resources
* [repo](https://github.com/Kevinoh47/lab-37)
* [codesandbox](https://codesandbox.io/s/o9o62ojoq5)
* [back-end for user data](http://localhost.com:3000)
* [back-end for teams data](https://javascript-401-api.herokuapp.com)

### Modules
#### `auth.js`
##### Exported Values and Methods
The /src/components/auth/auth.js file builds the auth class component, which is one of two LoginContext consumer components.

This class builds wraps its return statement in the <LoginContext.Consumer > component function. Inside this wrapper is a function, which takes context and tests the user's token to verify it and then compare the user's reported capabilities against whatever capability is required by any component that makes use of this function.

#### `context.js`
##### Exported Values and Methods
the /src/components/auth/context.js file builds the LoginProvider class. This class provides state to the props of any child components wrapped in its LoginContext.Provider function (if they are listeners via the LoginContext.Consumer function).

The state that is made available includes a boolean LoggedIn which describes whether the user is logged in or not, the user token, and methods for logging in and logging out.

#### `login.js`
##### Exported Values and Methods
the /src/components/auth/login.js file builds and exports the Login class component for actually logging the user in. This component wraps its functionality in the LoginContext.Consumer function, which takes context provided by the context store, and uses it to build a page for logging in and out of the site.

#### `if.js`
##### Exported Values and Methods
/src/components/if/index.js file builds and exports the If component which takes props, and tests for whether a condition on those props is true or false. If true, children components wrapped in the If compoenent will be rendered.

#### `actions.js`
##### Exported Values and Methods
The /src/components/record/actions.js file defines and exports the action functions post, get put, and destroy. These functions are all curried to be able to first run an async function, then when that is returned, dispatch the underlying action via the redux-thunk middleware.

#### `list.js`
##### Exported Values and Methods
The /src/components/record/list.js file builds and exports the Records class component. This component renders a set of records returned from a database call that is made after the component is rendered, via the componentDidMount lifecycle hook. It also creates methods for deleting and editing records, as well as resetting the record form. 

This component exports its functionality to the Redux store via the connect method, with input functions mapStateToProps and mapDispatchToProps. These functions push the records state to the Redux store and associate the methods to the redux dispatch actions.

The form that is rendered by this page uses LoginContext and the <Auth > component to manage what portions of the form are exposed to users of differing permissions/capabilities.

#### `record.js`
##### Exported Values and Methods
The /src/components/record/record.js creates and exports the Record class component, which renders a form for editing or creating a record. The form is based on a schema provided by the Redux store; the form is rendered dynamically based on this schema, by the Form component. The json schema is parsed by the react-jsonschema-form module.

#### `reducers.js`
##### Exported Values and Methods
The /src/components/record/reducers file provides the initialState that the actions will act upon. It then exports a function which takes state and action as inputs, parses the payload and action type from the action, and based on a switch statement, manages the response from the action.

#### `app.js`
##### Exported Values and Methods
The /src/components/app.js file builds and exports the App class component. This class contains a single render() method whhich returns a React Fragment, which contains the LoginContext component wrapping the Login component. App is the main controller of the application.

#### `store index.js`
##### Exported Values and Methods
The /src/store/index.js file exports the store function. This function combines the reducers, and applies middleware include the thunk middleware for managing ASYNC actions, and creates the redux store.

#### `index.js`
##### Exported Values and Methods
The /src/index.js file creates the Main function and renders it under the rootElement. The Main function returns the <App > component wrapped in the Redux provider, instantiated with the store created in the store() function from /src/store/index.js.


#### Tests
* How do you run tests?
* What assertions were made?
* What assertions need to be / should be made?

#### UML
Link to an image of the UML for your application and response to events
