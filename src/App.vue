<template>
  <div id="app">
  </div>
</template>

<script>
import * as monaco from "monaco-editor";

export default {
  name: "App",
  mounted() {
    monaco.editor.create(document.getElementById("app"), {
      value: [
        "function x() {",
        '\tconsole.log("Hello world!");',
        "}"].join(
        "\n"
      ),
      language: "javascript",
      theme: 'vs-dark',
      automaticLayout: true
    });
  }
};
</script>

<style>
html, body{
  margin: 0;
  padding: 0;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  height: 100vh;
  width: 800px;
  margin: 0;
  padding: 0;
  overflow: hidden;
}
</style>
