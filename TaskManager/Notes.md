# Vue 3 Core Concepts: Lifecycle Hooks, Template Refs, and watchEffect

## Table of Contents
- [Lifecycle Hooks](#lifecycle-hooks)
  - [The mounted() Hook](#the-mounted-hook)
  - [Other Important Hooks](#other-important-hooks)
- [Template Refs](#template-refs)
  - [Usage and Examples](#usage-and-examples)
  - [Common Use Cases](#common-use-cases)
- [watchEffect](#watcheffect)
  - [Basic Usage](#basic-usage)
  - [Key Features](#key-features)

## Lifecycle Hooks

Lifecycle hooks in Vue 3 are special functions that allow you to execute code at specific stages of a component's lifecycle. These hooks provide precise control over when certain operations should occur, from component creation to destruction.

### The mounted() Hook

The `mounted()` hook executes after the component is fully created and added to the DOM. This is particularly useful when you need to interact with the rendered DOM elements.

```javascript
export default {
  mounted() {
    console.log("Component mounted to DOM!");
    // Access DOM elements or perform DOM-dependent operations
  }
}
```

### Other Important Hooks

Vue 3 provides several other crucial lifecycle hooks:

```javascript
export default {
  created() {
    console.log("Component created!");
    // Component instance created, but DOM not yet mounted
  },
  
  updated() {
    console.log("Component updated!");
    // Runs after component's reactive data changes
  },
  
  destroyed() {
    console.log("Component destroyed!");
    // Clean up resources or remove event listeners
  }
}
```

## Template Refs

Template refs provide a way to directly reference DOM elements within your Vue templates. They create a bridge between your template and component logic, enabling direct DOM manipulation when necessary.

### Usage and Examples

Here's a practical example of using template refs:

```html
<template>
  <input ref="inputField" type="text" placeholder="Enter text">
  <button @click="focusInput">Focus Input</button>
</template>

<script>
export default {
  methods: {
    focusInput() {
      this.$refs.inputField.focus();
    }
  }
}
</script>
```

### Common Use Cases

Template refs are particularly valuable for:

1. Direct DOM element manipulation
2. Managing input field focus states
3. Implementing custom form validations
4. Triggering native DOM events or animations
5. Integrating with third-party libraries that require DOM access

## watchEffect

`watchEffect` is a powerful Vue 3 reactivity system feature that automatically tracks and responds to reactive dependencies within its execution block.

### Basic Usage

Here's how to implement `watchEffect`:

```javascript
import { ref, watchEffect } from 'vue'

export default {
  setup() {
    const count = ref(0)
    
    watchEffect(() => {
      console.log(`Count has changed to: ${count.value}`)
      // This will automatically re-run when count changes
    })
    
    return { count }
  }
}
```

### Key Features

`watchEffect` offers several advantages:

1. **Automatic Dependency Tracking**
   - Automatically detects and tracks reactive dependencies
   - No need to explicitly declare watched variables

2. **Immediate Execution**
   - Runs immediately upon creation
   - Perfect for side effects that need to happen right away

3. **Clean-up Handling**
   ```javascript
   watchEffect((onCleanup) => {
     const timer = setInterval(() => {
       // Some operation
     }, 1000)
     
     onCleanup(() => clearInterval(timer))
   })
   ```

## Best Practices

1. **Lifecycle Hooks**
   - Use `created()` for data initialization
   - Reserve `mounted()` for DOM-dependent operations
   - Implement clean-up in `destroyed()`

2. **Template Refs**
   - Use sparingly and only when necessary
   - Prefer Vue's reactive system when possible
   - Always check if ref exists before using

3. **watchEffect**
   - Keep effects focused and simple
   - Use cleanup function for resource management
   - Consider using `watch` for more specific dependency tracking

## Conclusion

Understanding these Vue 3 concepts is crucial for building robust applications:

- **Lifecycle Hooks** provide timing control over component operations
- **Template Refs** enable direct DOM access when necessary
- **watchEffect** offers automated reactive dependency tracking
