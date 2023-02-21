# React Framework

## JSX
* A syntax extension to JavaScript. In layman's terms, it is a combination of HTML and JavaScript. JSX produces React components.
* Valid JavaScript can be passed in to JSX via curly brackets.
* Hierarchicaly, it behaves in the same way as HTML: components can be passed in as children to other components.
* Some HTML attributes are not the same, such as class -> className.
* JSX Represents Objects: JSX boils down to React.createElement() calls. Babel takes care of converting JSX into said expression.
* JSX Cheatsheet: https://jsx-notes.vercel.app/

## Component
* Allow splitting pieces of the UI into independent, reusable pieces.
* Props: JSX attributes and children defined when calling a component.
* ReactDOM.createRoot(): takes a DOM element and turns it into the "root" element.
* root.render(): Takes in a parent React component and recursively renders it and it's children
 
## Props
* Objects can't be displayed but can be passed in as props

## How React Starts Up
* All of the project's JS files are bundled together into a single file, then placed onto a server. This is called a "bundle."
* The browser receives the index.html, the browser then makes the request for the bundled JS file.
* The bundled JS file finds the div with id of 'root' in the DOM, tells React to take control of that element, then tells React to get JSX from the App component, turn it into HTML and show it in the root div.
* useState: a function that works with React's "state" system. State is *like* a variable in React. State is used to store data that changes over time. Whenever state changes React automatically updates content on the screen.

## Libraries
* **React**: library that defines what a component is and how multiple components work together
* **ReactDOM**: Library that knows how to get a component to show up in the browser
 
## ES6 Modules (import/export statements)
* Export Statements:
    * Two kinds: 'default' and 'named'
    * Default Exports:
        * A file can only have a single 'default' export
        * There are two ways to write a default export:
        ```javascript
        export default function App() {}

        \\ or

        function App() {}
        export default App

        ```
        * Note: The latter is useful because you can edit the variable before exporting
    * Named Exports:
        * Use when exporting multiple variables
        * Can have as many named exports as we want
        * Two ways to write a named export
        ```javascript
       export const message = 'hi' 
       
       \\or
       
       const message = 'hi'
       export {message}
        ```
* Import Statements:
    * Importing default exports (Behind the Scenes):
            1. declare a variable called App
            2. find the default export from App.js
            3. assign the default export to App variable
        ```javascript
        import App from './App'
        ```
    * Note: Default export can be renamed in the importing file
    * Importing named exports:
        * Curly braces indicate we want a 'named' export
        * Single import statement can get both default + named exports
        * Named exports can be renamed using *as* keyword
        ```javascript
        import App, {message} from './App'
        \\ or
        import App, {message as myMessage} from './App'
        ```
    * Syntax:
        * './' or '../' means we are importing a file that we created
        * No './' or '../' means we are importing a package

## Images
* Importing images:
```javascript
import MyImage from './path/to/image.png'
```
* If image is less than 9.7kb (10,000 bytes), gets converted to base64 and is referenced inline.
* If image is more than above size, gets treated as separate file. 
```html
<img src="data:image/png;base64,ivjkdalvk"/>
<!-- versus -->
<img src="/static/media/myimage.png"/>
```

## CSS
* Importing .css
```javascript
// importing a CSS from an npm module 
import 'bulma/css/bulma.css'
// importing CSS from a local file
import './path/to/my.css'
```
* When importing CSS, the referenced CSS is put directly in a <style> tag in the <head> tag.

## Events
https://reactjs.org/docs/events.html
We make use of events anytime we want to be notified about the user interacting with our app in some way.
## Using Events
1. Decide what kind of event you want to watch for.
2. Create a function. *Usually called an event handler or callback function.*
3. Name the function using pattern of *(handle|on) + EventName* (recommended) i.e. handleClick
4. Pass the function as a prop to a plain element
5. Make sure you pass teh function using a valid event name (i.e. onClick, onMouseOver, etc.)
6. Make sure you pass a reference to the function (don't call it in the prop)

## State
State: Data that changes as the user interacts with our application.
When this data changes, React will update content on the screen automagically.
***This is the one-and-only way we can change what content React shows.***
### Using State
1. Define a piece of state with the useState function.
2. Give a value to the useState function. This is the default, starting value for our piece of state.
3. Use the state in some way in our component (often used in the returned JSX).
4. When the user does something, update the piece of state. Casues React to rerender the component.

## Handling Text Inputs
1. Create a new piece of state
2. Create an event handler to watch for the 'onChange' event
3. When the 'onChange' event fires, get the value from the input
4. Take that value from the input and use it to update your state
5. Pass your state to the input as the value prop

## Key Prop
* When rendering a dynamic list of elements, a 'key' prop is used for letting react know which elements can be reusded for the next render.
* React will compare the keys of the new element with the previous keys and then:
  1. mount components having a new key
  2. unmount components whose keys are not used anymore
* If there are no ID's to use, there are two fallbacks that can be used:
  * Use the index of the record (will lead to bugs as the list is updated)
  * Generate a unique ID yourself
* Requirements for keys:
  * Use whenever we have a list of elements
  * Add the key to the top-most JSX element in the list
  * Must be a string or number
  * Should be unique ***for this list***
  * Should be consistent across rerenders
