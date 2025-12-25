# Vue Review

This is a Vue Composition API רeview

## Table Of Content

- [Udemy course](#udemy-course)
- [Extensions](#extensions)
- [CSS](#css)
- [Featues and Code Samples](#featues-and-code-samples)

  - [Root Compoment](#root-component)
  - [ref()](#ref)
  - [computed()](#computed)
  - [conditional css class](#conditional-css-class)
  - [input binding](#input-binding)
  - [event handling](#event-handling)
    - [v-on](#v-on)
    - [modifiers](#modifiers)
  - [conditional rendering v-if](#conditional-rendering)
  - [list rendering v-for](#list-rendering)
  - [attribute binding](#attribute-binding)
  - [template refs, accesing DOM element ](#template-refs)
  - [watcher](#watcher)

- [Comments](#comments)

## Udemy course

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**

- [https://www.udemy.com/course/vue-in-action](https://www.udemy.com/course/vue-in-action)

## Extensions

- [https://marketplace.visualstudio.com/items?itemName=Vue.volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar)
- [https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)

## CSS

- Snadcn
- tailwind
- React/Next

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**

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

```
<div v-for="task in tasks" :key="task.id"
            :class="{'task':true, completed: task.done, [task.priority.toLowerCase()]: true}"
>
</div>
```

### Input Binding

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**

```
<input v-model="age" />

setup() {
  let age = ref(null);
}
```

### Event Handling

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**

```
setup() {
  const addPhoto = () => {
    console.log('addPhoto');
  };
  return { addPhoto };
}
```

#### v-on

```
<button type="submit" v-on:click="addPhoto">Add Photo</button>

<button type="submit" @click="addPhoto">Add Photo</button>
```

#### modifiers

```
<form @submit.prevent="addPhoto">
</form>
```

## Conditional Rendering

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**

```
<div class="no-photos" v-if="photos.length === 0"><\div>
<div class="gallery" v-else><\div>

setup() {
  const photos = ref([]);
  return { photos,};
}
```

## List Rendering

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**

```
<div class="photo" v-for="photo in photos">
  {{ photo.id }}
</div>

<li v-for="({ message }, index) in items">
  {{ message }} {{ index }}
</li>

<li v-for="item in items">
  <span v-for="childItem in item.children">
    {{ item.message }} {{ childItem }}
  </span>
</li>
```

### Attribute Binding

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**

```
<div v-bind:id="dynamicId"></div>
<div :id="dynamicId"></div>
```

### Template Refs

```
<div id="app">
  <form>
    <input ref="newTaskInput" placeholder="Add new task" />
  </form>
</div>

setup() {
  const newTaskInput = ref(null);

  onMounted(() => {
    console.log('onMounted');
    newTaskInput.value.focus();
    }
  );
}
```

### watcher

Perform action in reaction to reactive property state change

```
watch(newTask, (newValue, oldValue) => {
  console.log({ newValue, oldValue });
});

watch(tasks,() => {
  console.log('tasks are changed');
  },
  { deep: true, immediate: true }
);
```

- deep - watch for deep changes
- immideate - invoke watch handler immidiatle and in change
- watchEffect

  ```
  watchEffect(() => {
    console.log('New task value is: ' + newTask.value);
  });
  ```

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**

## Comments

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**
