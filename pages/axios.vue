<template>
  <section class="container">
    <h1>{{title}}</h1>
    <p>{{message}}</p>
    <pre>{{html_data}}</pre>
  </section>
</template>

<script>
  const axios = require('axios');

  let url = "/README.md";

  export default {
    data: function(){
      return {
        title: 'Axios',
        message: 'axios sample',
      };
    },
    asyncData: async function(){
      let result = await axios.get(url);
      return {html_data: result.data};
    },
  }
</script>

<style>
.container {
  padding: 5px 10px;
}
h1 {
  font-size: 60px;
  color: #345980;
}
p {
  padding-top: -5px;
  font-size: 20px;
}
div {
  font-size: 14px;
}
pre {
  padding: 10px;
  font-size: 18px;
  background-color: #efefef;
  word-spacing: pre-wrap;
}
hr {
  margin: 10px 0;
}
</style>


