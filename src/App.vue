<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" width="25%" />
    <div
      style="
        display: flex;
        flex-direction: column;
        justify-content: cneter;
        align-items: center;
      "
    >
      <template v-for="item in columns">
        <div
          :key="item.key"
          style="display: flex; flex-direction: row; padding: 8px 0"
        >
          <label :for="item.key" style="padding-right: 10px">{{
            item.key
          }}</label>
          <HelloWorld v-model="form" :type="item.type" :path="item.path" />
        </div>
      </template>
    </div>
    {{ form }}
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
  data() {
    return {
      form: {
        a: {
          b: {
            c: 1,
          },
        },
        d: "1231",
      },
      columns: [
        {
          key: "accounnt",
          path: "a.b.c",
          type: "input",
        },
        {
          key: "commend",
          path: "d",
          type: "number",
        },
      ],
    };
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
