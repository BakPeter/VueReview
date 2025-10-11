Vue Composition API

- [Udemy course](#udemy-course)
- [Extensions](#extensions)
- [Code Templates](#code-templates)
  - [Root Compoment](#root-component)
- [Comments](#comments)

## Udemy course

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**

- [https://www.udemy.com/course/vue-in-action](https://www.udemy.com/course/vue-in-action)

## Extensions

- [https://marketplace.visualstudio.com/items?itemName=Vue.volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar)
- [https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer](https://marketplace.visualstudio.com/items?itemName=ritwickdey.LiveServer)

## Code Templates

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

## Comments

**[`^ top ^`](#vue-review)** | **[`^ Table of content ^`](#table-of-content)**
