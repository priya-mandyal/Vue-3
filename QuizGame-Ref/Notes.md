# Vue.js Reference Notes

## Reactivity with `ref`
The `ref` function is used to make values reactive in Vue. When a ref's value changes, any components using that value will automatically update.

```javascript
let message = ref("hi");

// To change the value, use .value property
message.value = "Bye";
// UI will automatically update to show "Bye"
```

## Computed Properties
`computed()` creates a reactive value that automatically recalculates when its dependencies change.

```javascript
let age = ref(null);
let canDrive = computed(() => {
    return age.value >= 18 ? "Yes" : "No";
});
// canDrive will recalculate whenever age changes
```

## Basic Vue Application Structure
Here's the basic structure needed to start a Vue application:

```javascript
// Import required functions from Vue
const { createApp, ref } = Vue;

// Define the main App
const App = {
    // setup() is where application logic goes
    setup() {
        // Return values and methods to make them available in the template
        return {
            message: "Hello"
        }
    }
};
```

## Conditional CSS Classes
Vue provides dynamic class binding using `v-bind` or the shorthand `:`. Class bindings can be expressed through objects where:
- Keys are CSS class names
- Values are conditions determining if the class should be applied

Example:
```javascript
// In template
<div :class="{ 'active': isActive, 'error': hasError }">
```

## Form Input Binding
Vue uses the `v-model` directive to create two-way data binding on form inputs:

```html
<!-- Basic input binding -->
<input v-model="inputText">

<!-- The value of inputText will update automatically when the input changes -->
```

### Setup example:
```javascript
const App = {
    setup() {
        const inputText = ref('');
        
        return {
            inputText
        }
    }
}
```

### Key Points to Remember:
1. Always use `.value` when modifying ref values in JavaScript
2. Computed properties automatically track their dependencies
3. The `setup()` function must return any values or methods you want to use in the template
4. Class bindings can use objects or arrays for dynamic styling
5. `v-model` creates reactive two-way binding for form inputs
