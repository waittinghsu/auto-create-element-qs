<template>
  <div class="hellos">
    <input :type="type" @input="handleInput" />
  </div>
</template>

<script>
import { cloneDeep, set } from "lodash-es";
export default {
  name: "HelloWorld",
  model: {
    prop: "modelValue",
    event: "update",
  },
  props: {
    modelValue: {
      type: Object,
      default: () => {},
    },
    type: {
      type: String,
      default: "text",
    },
    path: {
      type: String,
      default: "text",
    },
  },
  data() {
    return {};
  },
  methods: {
    handleInput(event) {
      console.log(Object.prototype.toString.call(event), event.target.value);
      const modelValue = cloneDeep(this.modelValue);
      set(modelValue, this.path, event.target.value);
      this.$emit("update", modelValue);
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
