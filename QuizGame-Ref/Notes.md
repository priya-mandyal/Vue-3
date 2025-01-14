# Vue.js Reactivity and Concepts

## 1. **Ref in Vue**

- **Usage:** `ref` is used for creating reactive variables in Vue. It allows us to store values and track changes, updating the UI automatically when the value changes.

### Example:
```javascript
let message = ref("hi");
// To change, use .value
message.value = "Bye";
// This change will be automatically updated on the UI.
 2. Computed Properties
Usage: computed is used to create derived properties or values that depend on other reactive data. When the dependencies change, the computed property will automatically recalculate.
Example:
javascript
Copy code
let age = ref(null);
let canDrive = computed(() => {
  return age.value >= 18 ? "Yes" : "No";
});
// Whenever `age` value changes, `canDrive` will be recalculated.
3. Starter Code Explained
get createApp and ref from Vue: The createApp method is used to initialize a Vue application, and ref is used to create reactive variables.
javascript
Copy code
// Get createApp and ref from Vue
const { createApp, ref } = Vue;

// App is something you need to have to start with Vue
const App = {
  // setup is where your code/logic goes
  setup() {
    // All the methods you want to trigger or values you want to show need to be returned here
    return {
      message: "Hello"
    };
  },
};
4. Conditional CSS with v-bind
Usage: You can add conditional CSS classes using the v-bind directive (i.e., :). You can bind classes in various ways, such as with objects, arrays, or components. In this case, we are using an object where keys are the CSS classes and values are the conditions.
Example:
html
Copy code
<div :class="{ active: isActive, 'text-danger': hasError }">
  This will conditionally apply the CSS classes.
</div>
5. Form Input Binding
Usage: You can use v-model for two-way data binding in form elements (input fields, checkboxes, etc.). This means that whenever the value in the input changes, the Vue component's data will automatically reflect those changes.
Example:
html
Copy code
<input v-model="message" type="text" />
<!-- When you type in the input field, the `message` variable will be automatically updated. -->
Summary
Ref: Use for creating reactive variables.
Computed: Automatically recalculates values when dependencies change.
Conditional CSS: Bind CSS classes conditionally using :class.
Form Input Binding: Use v-model to bind form inputs to Vue data for two-way binding.
