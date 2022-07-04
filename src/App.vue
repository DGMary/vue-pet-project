<template>
  <div id="app">
    <el-tabs v-model="activeName">
      <el-tab-pane label="Users" name="first"
        ><TabUsers :todos-data="todosData"
      /></el-tab-pane>
      <el-tab-pane label="Table" name="second"
        ><TabTable :todos-data="todosData"
      /></el-tab-pane>
    </el-tabs>
  </div>
</template>

<script>
import TabUsers from "./components/TabUsers";
import TabTable from "./components/TabTable";
import axios from "axios";

export default {
  /**
   * Name.
   */
  name: "App",

  /**
   * Components
   */
  components: {
    TabUsers,
    TabTable,
  },

  /**
   * Mounted hook.
   */
  mounted() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos/")
      .then((response) => (this.todosData = response.data));
  },

  /**
   * Reactive properties.
   * @returns {{}}
   */
  data: function () {
    return {
      todosData: {},
      activeName: "first",
    };
  },
};
</script>

<style></style>
