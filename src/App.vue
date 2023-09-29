<!-- App.vue -->

<template>
  <div id="app">
    <div class="container">
      <div class="box">
        <ckeditor :editor="editor" v-model="editorData" :config="editorConfig"></ckeditor>
        <p>{{ editorData }}</p>
      </div>
    </div>
  </div>
</template>

<script>
// ⚠️ NOTE: We don't use @ckeditor/ckeditor5-build-classic any more!
// Since we're building CKEditor&nbsp;5 from source, we use the source version of ClassicEditor.
import { ClassicEditor } from '@ckeditor/ckeditor5-editor-classic'

import { Alignment } from '@ckeditor/ckeditor5-alignment' // Importing the package.
import { List } from '@ckeditor/ckeditor5-list'
import { ListProperties } from '@ckeditor/ckeditor5-list'
import { Table, TableToolbar } from '@ckeditor/ckeditor5-table'
import { Essentials } from '@ckeditor/ckeditor5-essentials'
import { Bold, Italic } from '@ckeditor/ckeditor5-basic-styles'
import { Link } from '@ckeditor/ckeditor5-link'
import { Paragraph } from '@ckeditor/ckeditor5-paragraph'

export default {
  name: 'app',
  data() {
    return {
      editor: ClassicEditor,
      editorData: '<p>Content of the editor.</p>',
      editorConfig: {
        plugins: [
          Alignment,
          List,
          ListProperties,
          Table,
          TableToolbar,
          Essentials,
          Bold,
          Italic,
          Link,
          Paragraph
        ],

        toolbar: {
          items: [
            'alignment', // Displaying the proper UI element in the toolbar.
            'bulletedList',
            'numberedList',
            'insertTable',
            'bold',
            'italic',
            'link',
            'undo',
            'redo'
          ]
        },

        list: {
          properties: {
            styles: true,
            startIndex: true,
            reversed: true
          }
        },
        table: {
          contentToolbar: ['tableColumn', 'tableRow', 'mergeTableCells']
        }
      }
    }
  }
}
</script>
<style>
.container {
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  width: 100%;
  margin: 0;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
}
.box {
  width: 600px;
}
.ck-content {
  height: 300px;
}
</style>
