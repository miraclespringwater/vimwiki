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
