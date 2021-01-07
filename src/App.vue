<template>
  <main id="app">
    <h1>Welcome, Json Editor Test App</h1>
    <json-editor
      :initialJson="jsonData"
      @updateData="setJsonData"
      class="border"
    ></json-editor>
    <section class="border">
      <h2>Updated Json Data</h2>
      <pre>{{ jsonData }}</pre>
    </section>
  </main>
</template>

<script>
import JsonEditor from "./components/JsonEditor.vue";

export default {
  name: "App",
  components: {
    JsonEditor
  },
  data() {
    return {
      jsonData: {
        dummy: "data"
      }
    };
  },
  methods: {
    setJsonData(data) {
      this.jsonData = data;
    }
  }
};
</script>

<style>
section {
  text-align: left;
  padding: 30px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.border {
  margin: 20px;
  border-color: darkgrey;
  border-style: solid;
  border-radius: 5px;
}
</style>
