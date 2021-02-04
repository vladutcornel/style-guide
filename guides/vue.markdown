---
layout: page
title: Vue guidelines
---

Vue.js has its own [style guide](https://vuejs.org/v2/style-guide/) which you should follow. I am just going to add to it.

Do not follow this guide
------------------------
If you are joining an existing project and team, chances are there are already style guides that your team follows.  
Ask your Team Leader about them. Only if there aren't any, or you feel comfortable in suggesting changes,
ask them if they are willing to follow this guide.

Always use Vue Component files
------------------------------
Vue allows defining templates directly in HTML. This should be avoided at all costs. Take the time to set up Webpack and a JS build system. 

Use Webpack [Aliases](https://webpack.js.org/configuration/resolve/#resolvealias)
-------------------
New Vue projects may already have the source folder aliased as `@`, but you may need to add it to existing projects.  
Add any other aliases for folders that you use often

```js
<!-- BAD -->
import BaseButton from "../../../shared/BaseButton";
import BaseList from "../../shared/BaseList/Index";

<!-- Good -->
import BaseButton from "@/shared/BaseButton";

<!-- Stretched, but Good enough -->
import BaseList from "@BaseList/Index";

```

Folder structure
----------------
Your sources folder should have two sub-folders dedicated to Vue components:

- `screens` or `pages` for screens referenced by the [router](https://router.vuejs.org/).
    - Screens should be distributed in folders in a way that makes sense for the project
    - If a screen needs sub-components that can not be shared, the screen should be defined in a folder that contains `Index.vue` and a `components` sub-folder
    - If a screen has sub-screens (i.e. screens that can not be accessed from anywhere else), it should be defined as a folder that contains `Index.vue` and the sub-screens following the same rules. 
    - If the screen only uses shared components, it can be defined in a single Vue file
- `shared` for components used by multiple screens
    - If the shared component uses sub-components that do not make sens in other components, it should be defined as a folder that contains `Main.vue` and the sub-components.
    - If a shared component is not using exclusive sub-components, it can be defined ina single Vue file.

If you don't know if a component will be reused, make it a screen sub-component, then make it shared in the future when you need to reuse it.

The name of the component should concatenate parent component names

Example:
```
screens
|-- Blog
|   |-- components
|   |   '-- Excerpt.vue         (Tag: BlogExcerpt)
|   |-- Post
|   |   |-- components
|   |   |   |-- Title.vue       (Tag: BlogPostTitle)
|   |   |   '-- Comments.vue    (Tag.BlogPostComments)
|   |   |-- Index.vue           (Tag: BlogPost)
|   '-- Index.vue               (Tag: BlogScreen)
|-- About.vue
'-- Home.vue

shared
|-- BaseList
|   |-- Item.vue    (Tag: BaseListItem)
|   '-- Main.vue    (Tag: BaseList)
'-- BaseButton.vue  (Tag: BaseButton)
```

No logic in template
--------------------
The Vue Style Guide recommends using [simple expressions in templates](https://vuejs.org/v2/style-guide/#Simple-expressions-in-templates-strongly-recommended).

There should be absolutely no logic in the expressions in the `<template>` section.
Use computed properties and methods for absolutely any expression that involves any kind of operator.

```vue
<!-- BAD -->
<div v-if="valid && 'test' === stage"></div>
<div v-if="'test' === stage"></div>

<!-- Good -->
<div v-if="isValidTesting"></div>
<div v-if="isTesting"></div>
```

When to change the state
------------------------
By "state", I mean the current set of data values in a component.

Computed properties should only return a value based on the current state. They should never change the state.

Methods should change the state only when referenced as an event listener.

#### Bad
```vue
<template>
    <button>{{ buttonText }}</button>
</template>
<script>
export default {
    data: ()=> ({
        count: 0
    }),
    computed: {
        buttonText() {
            const current = this.count;
            
            this.count++; // DO NOT DO THIS.
            
            switch (current) {
                case 0: return "Never pressed";
                case 1: return "Pressed once";
            }
            
            return `Pressed ${current} times`;
        }
    }
}
</script>
```