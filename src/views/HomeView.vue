<template>
  <div class="contents">
    <textarea id="json" v-model="json"></textarea>
  </div>
  <div class="content">
    <Codemirror
      v-model:value="code"
      :options="cmOptions"
      border
      placeholder="test placeholder"
      :height="575"
      :width="620"
      @change="change"
    />
    <pre class="code">{{ json }}</pre>
  </div>
</template>
<script>
import Codemirror from "codemirror-editor-vue3";

// language
import "codemirror/mode/javascript/javascript.js";

// theme
import "codemirror/theme/dracula.css";

import { ref } from "vue";
export default {
  components: { Codemirror },
  setup() {
    const json = ref("Enter Json Here");
    const code = ref(`
var i = 0;
for (; i < 9; i++) {
  console.log(i);
  // more statements
}`);

    return {
      code,
      json,
      cmOptions: {
        mode: "text/javascript", // Language mode
        theme: "dracula", // Theme
        lineNumbers: true, // Show line number
        smartIndent: true, // Smart indent
        indentUnit: 2, // The smart indent unit is 2 spaces in length
        foldGutter: true, // Code folding
        styleActiveLine: true, // Display the style of the selected row
      },
    };
  },
};
</script>
<style>
.content {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  height: 100vh;
}
#json {
  width: 30vw;
  height: 20vh;
  margin: 0 1rem;
  border: 1px solid #ddd;
}
/* center .contents div childs */
.contents {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: center;
  height: 20vh;
}
#contents {
  margin-top: 5px;
}
.code,
.codemirror .cm-editor {
  width: 30vw;
  height: 50vh;
  margin: 0 1rem;
  border: 1px solid #ddd;
  overflow: scroll;
}
.CodeMirror {
  font-family: Arial, monospace;
  font-size: 16px;
}
</style>
