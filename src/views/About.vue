<template>
  <div v-if="result" class="About">
    <h1>This is an about page</h1>
    <p>user ID: {{ result.userId }}</p>
    <p>title: {{ result.title }}</p>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data: () => ({
    result: null,
  }),
  created() {
    let post = {
      title: "2005045",
      body: "<p>Example2005045</p>",
      userId: 1,
    };
    let post_update = {
      title: "2005045",
      body: "<p>Example2005045</p>",
      userId: 1,
    };
    axios.get("https://jsonplaceholder.typicode.com/todos/1").then((result) => {
      this.result = result.data;
      //console.log(result.data);
    }),
      axios
        .post("https://jsonplaceholder.typicode.com/posts", post)
        .then((result) => {
          console.log(result);
        }),
      axios
        .put("https://jsonplaceholder.typicode.com/posts", post_update)
        .then((result) => {
          console.log(result);
        });
  },
};
</script>