# Vue Review

This is a Vue Composition API רeview

## Table Of Content

- [Udemy course](#udemy-course)
- [Extensions](#extensions)
- [Featues and Code Samples](#featues-and-code-samples)
  - [Root Compoment](#root-component)
  - [ref()](#ref)
  - [computed()](#computed)
  - [conditional css class](#conditional-css-class)
  - [input binding](#input-binding)
- [Comments](#comments)

## Udemy course

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**

- [https://www.udemy.com/course/vue-in-action](https://www.udemy.com/course/vue-in-action)

## Extensions

- [https://marketplace.visualstudio.com/items?itemName=Vue.volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar)
- [https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)

## Featues and Code Samples

### Root Component

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**

The mount() method is called. It expects a "container" argument, which can either be an actual DOM element or a selector string.

The content of the app's root component will be rendered inside the container element. The container element itself is not considered part of the app

```
<div id="app"></div>
```

```
import { createApp } from 'vue'
import App from './App.vue'

const app = createApp(App)
app.mount('#app')

```

### ref()

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**

ref() is a function used to create a reactive reference to a value — that is, a piece of reactive state that Vue tracks and updates the DOM when it changes.

```
<template>
  <button @click="count++">
    Count is: {{ count }}
  </button>
</template>

<script setup>
import { ref } from 'vue'

const count = ref(0)
</script>
```

### computed()

computed() is used to define reactive, derived values — values that are automatically calculated from other reactive data (ref, reactive, etc.) and update whenever their dependencies change.

```
<script setup>
import { ref, computed } from 'vue'

const count = ref(2)

const double = computed(() => count.value * 2)

const plusOne = computed({
  get: () => count.value + 1,
  set: (val) => {
    count.value = val - 1
  }
})
</script>

<template>
  <p>Count: {{ count }}</p>
  <p>Double: {{ double }}</p>
  <button @click="count++">Increment</button>
</template>
```

### Conditional CSS Class

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**

```
<span :class="{can: canDrive === 'YES', cant: canDrive === 'NO'}">{{ canDrive }}</span>

let canDrive = computed(() => {
  console.log('Computed Invoked');
  return age.value >= 18 ? 'YES' : 'NO';
});
```

### Input Binding

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**

```
<input v-model="age" />

setup() {
  let age = ref(null);
}
```

## Comments

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**
