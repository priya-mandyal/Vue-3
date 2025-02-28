# Vue.js Overview

## What is Vue.js?

Vue.js is a frontend framework that simplifies the development of interactive and reactive websites. It reduces the amount of boilerplate code needed to build dynamic applications and makes the code more manageable and easier to read.

For example, in JavaScript, you would need to write longer code to create a button that increments a counter and displays it. However, Vue.js provides built-in functionality to make this task more concise.

### Vue.js is Declarative and Reactive

- **Declarative**: In Vue.js, you tell the framework **what** the UI should look like, and Vue takes care of updating the DOM for you. 
  - Example: `<p> {{ message }} </p>`. 
    You simply declare `{{ message }}`, and Vue will render the value of `message` in the UI. You don't need to worry about manually manipulating the DOM.

- **Reactive**: Vue.js automatically updates the DOM when the value of a declared property changes. 
  - In traditional JavaScript, you need to write code to update the DOM manually. 
  - With Vue, once you change the value of a variable like `message`, it automatically updates the UI.
  
### Watch Option in Vue.js

Vue.js provides the `watch` option, which allows you to **respond to changes in specific data properties**. It is particularly useful when you need to perform some action or side effect when the value of a watched property changes.

#### Example:

```js
watch: {
  name(oldValue, newValue) { // 'name' is the watched property
    // Code to perform when 'name' changes
  }
}
```
### VS Code Shortcuts

- CMD + P: Open a file.
- CMD + Shift + P: Run a command.
- CMD + B: Hide the left panel.
- Ctrl + `: Open terminal.
