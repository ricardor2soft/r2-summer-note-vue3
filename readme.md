# Vue3 Summernote Editor

A VueJs 3 component for use [Summernote WYSIWYG](https://summernote.org/)

## Install
``` cmd
// npm install
npm install r2-summer-note-vue3 --save
```

You must be have `jQuery` at `window.$` and install summernote by yourself.

### Use as component
1. import as global component.
``` javascript
// import SummernoteEditor
import SummernoteEditor from 'r2-summer-note-vue3';


const vueApp = createApp({});
vueApp.component('SummernoteEditor', SummernoteEditor);

```

2. import into a single component.
``` javascript
// import SummernoteEditor
import SummernoteEditor from 'r2-summer-note-vue3';

<template>
  <SummernoteEditor
      v-model="myValue"
      @update:modelValue="summernoteChange($event)"
      @summernoteImageLinkInsert="summernoteImageLinkInsert"
    />
</template>
<script>
export default {
    // declare SummernoteEditor
    components: {SummernoteEditor},
    data() {
        return {
            myValue: '',
        }
    },
    methods: {
       summernoteChange(newValue) {
          console.log("summernoteChange", newValue);
       },
        summernoteImageLinkInsert(...args) {
          console.log("summernoteImageLinkInsert()", args);
       },
    }
}
</script>
```


### Options
- `options`: `option[]`
  - configurable settings, see [Summernote options](https://summernote.org/deep-dive/)
  - you can define a global options on a `window.SUMMERNOTE_DEFAULT_CONFIGS`

### Events
- `update:modelValue`
  - triggered when summernote value change
- `summernote bare events`
  - summernote events will be triggered in camelCase
  - `"summernote.change": "summernoteChange"`
  - `"summernote.image.link.insert": "summernoteImageLinkInsert"`
