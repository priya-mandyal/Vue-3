# Vue 3 Concepts: Lifecycle Hooks, Template Refs, and `watchEffect`

## Lifecycle Hooks in Vue 3

Lifecycle hooks in Vue are special functions that allow you to run code at particular lifecycle events of a component. These events can include creation, mounting, updating, and destruction of the component.

### Example of `mounted()` Lifecycle Hook

The `mounted()` hook runs when the component is fully created and added to the DOM (screen). You can use this hook to execute code that requires access to the DOM.

```javascript
export default {
  mounted() {
    console.log("Component mounted to DOM!");
  }
};

In the above example, the message "Component mounted to DOM!" will be logged to the console when the component is fully mounted.

Other Lifecycle Hooks
created(): Runs after the component instance is created but before mounting begins.
updated(): Runs whenever the component's reactive data changes.
destroyed(): Runs when the component is about to be destroyed.
Example:

javascript
Copy
Edit
export default {
  created() {
    console.log("Component created!");
  },
  updated() {
    console.log("Component updated!");
  },
  destroyed() {
    console.log("Component destroyed!");
  }
};
Template Refs
Template refs are a way of referencing DOM elements directly in your Vue template, which can then be accessed and manipulated within your Vue component's script.

Example of Using Template Refs
html
Copy
Edit
<template>
  <input ref="inputField" type="text" placeholder="Enter text">
  <button @click="focusInput">Focus Input</button>
</template>

<script>
export default {
  methods: {
    focusInput() {
      // Accessing the input field using ref and focusing it
      this.$refs.inputField.focus();
    }
  }
};
</script>
In the above example:

We use the ref="inputField" to reference the input element in the template.
The focusInput() method accesses the input element using this.$refs.inputField and calls .focus() to focus on the input when the button is clicked.
Use Cases for Template Refs
Directly accessing DOM elements.
Managing focus on input fields.
Triggering animations or transitions.
watchEffect in Vue 3
watchEffect is a Vue 3 function that automatically tracks reactive dependencies and runs whenever any of them change. It is useful for scenarios where you need to automatically react to changes in reactive data.

Example of watchEffect
javascript
Copy
Edit
import { ref, watchEffect } from "vue";

export default {
  setup() {
    const count = ref(0);

    // watchEffect automatically tracks 'count'
    watchEffect(() => {
      console.log(`Count has changed to: ${count.value}`);
    });

    return { count };
  }
};
In this example:

watchEffect is used to automatically track the reactive count variable.
Whenever the value of count changes, the function inside watchEffect is re-executed, logging the updated value to the console.
Key Features of watchEffect
Automatically tracks all reactive dependencies within the function.
Re-runs the effect whenever any of the reactive dependencies change.
Does not require an explicit list of dependencies like watch does.
Conclusion
Lifecycle Hooks: mounted(), created(), updated(), and other hooks allow you to run specific code at different stages of a component's lifecycle.
Template Refs: Template refs help you directly access and manipulate DOM elements in the template from the Vue component script.
watchEffect: This function makes it easy to react to changes in reactive data, automatically tracking dependencies and re-running code when they change.
