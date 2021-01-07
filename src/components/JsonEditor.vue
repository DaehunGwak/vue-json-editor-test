<template>
  <section>
    <h2>JsonEditor</h2>
    <div ref="jsoneditor"></div>
  </section>
</template>

<script>
import JSONEditor from "jsoneditor/dist/jsoneditor.min.js";
import "jsoneditor/dist/jsoneditor.min.css";

export default {
  name: "JsonEditor",
  props: {
    options: {
      type: Object,
      required: false,
      default: () => {
        return {
          mode: "code"
        };
      }
    },
    initialJson: {
      type: Object,
      required: false,
      default: () => {
        return {};
      }
    }
  },
  data() {
    return {
      editor: null,
      data: {}
    };
  },
  mounted() {
    const options = {
      ...this.options,
      onChangeText: jsonString => {
        try {
          this.data = JSON.parse(jsonString);
          this.$emit("updateData", this.data);
        } catch (e) {
          if (!(e instanceof SyntaxError)) {
            throw e;
          }
        }
      }
    };
    this.data = this.initialJson;
    this.editor = new JSONEditor(this.$refs.jsoneditor, options, this.data);
  }
};
</script>

<style scoped></style>
