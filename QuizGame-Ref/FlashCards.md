# Vue 3 Composition API Basics

## **Ref**
### **Usage**:
To create a reactive variable in Vue.

### **Access**:
We can access or change it using `.value`.

### **Code Example**:
```javascript
const count = ref(0); // Declare a reactive variable
count.value = 2;      // Modify the value
```

---

## **Computed**
### **Usage**:
Creates a reactive derived value based on another reactive value. Whenever the base reactive value is altered, the computed property updates automatically.

### **Access**:
Uses `.value` to access the computed value.

### **Code Example**:
```javascript
const num = ref(0);
const count = computed(() => {
  return num.value + 1;
});

console.log(count.value); // Outputs: 1
num.value = 5;
console.log(count.value); // Outputs: 6
```

---

## **Accessible Return**
### **Usage**:
Returns the variables and methods in `setup()` to make them available in the template.

### **Code Example**:
```html
<template>
  <div>{{ count }}</div>
</template>

<script>
import { ref } from 'vue';
export default {
  setup() {
    const count = ref(0);
    return {
      count
    };
  }
};
</script>
```

---

## **v-model**
### **Definition**:
Two-way binding between a variable and an input field.

### **Code Example**:
```html
<template>
  <input v-model="count" />
  <p>{{ count }}</p>
</template>

<script>
import { ref } from 'vue';
export default {
  setup() {
    const count = ref(0);
    return {
      count
    };
  }
};
</script>
```

---

## **Add a Method to a Button**
### **Usage**:
Attach a button to a click event using `@click`.

### **Code Example**:
```html
<template>
  <button @click="display">Display</button>
</template>

<script>
import { ref } from 'vue';
export default {
  setup() {
    const message = ref("Hello, Vue!");

    const display = () => {
      alert(message.value);
    };

    return {
      display
    };
  }
};
</script>
