#CKEditor 5 classic editor with Simple Upload Adapter

##Quick start for NUXT.JS

First, install the build from npm:
```bash
yarn install @ckeditor/ckeditor5-vue;
@honglm/ckeditor5-build-simple-upload;
```

Create ckeditor.js in `/plugins` folder
```js
import Vue from 'vue';
import CKEditor from '@ckeditor/ckeditor5-vue';

export default () =>{
    Vue.use(CKEditor);
}
```

In nuxt.config.js
```js
plugins: [
    '@/plugins/ckeditor.js'
]
```

And use it in your pages:

```html
<template>
	<div class="links">
	<ckeditor :editor="editor" v-model="editorData" :config="editorConfig"></ckeditor>
	</div>
</template>


<script>
import ClassicEditor from "@honglm/ckeditor5-build-simple-upload";
export default {
  components: {},
  data() {
    return {
      editor: ClassicEditor,
      editorData: "<p>Content of the editor.</p>",
      editorConfig: {
        simpleUpload: {
          // The URL that the images are uploaded to.
          uploadUrl: "http://example.com",

          // Enable the XMLHttpRequest.withCredentials property.
          withCredentials: true,

          // Headers sent along with the XMLHttpRequest to the upload server.
          headers: {
            "X-CSRF-TOKEN": "CSFR-Token",
            Authorization: "Bearer <JSON Web Token>"
          }
        }
      }
    };
  },
  mounted() {}
};
</script>
```



