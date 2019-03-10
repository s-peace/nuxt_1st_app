<template>
  <section class="container">
    <h1>{{title}}</h1>
    <p>{{message}}</p>
    <div>
      <input type="text" v-model="msg">
      <button @click="doClick">Click</button>
    </div>
    <table>
      <tr>
        <th>User ID</th>
        <td>{{json_data.userId}}</td>
      </tr>
      <tr>
        <th>ID</th>
        <td>{{json_data.id}}</td>
      </tr>
      <tr>
        <th>Title</th>
        <td>{{json_data.title}}</td>
      </tr>
      <tr>
        <th>Body</th>
        <td>{{json_data.body}}</td>
      </tr>
    </table>
  </section>
</template>

<script>
  const axios = require('axios');

  let url = "https://jsonplaceholder.typicode.com/posts/";

  export default {
    data: function(){
      return {
        title: 'Axios',
        message: 'axios sample',
        msg: '',
        json_data: {},
      };
    },
    methods: {
      doClick: function(event){
        axios.get(url + this.msg).then((res) => {
          this.message = 'get ID=' + this.msg;
          this.json_data = res.data;
        }).catch((error) => {
          this.message = 'ERROR!';
          this.json_data = {};
        })
      }
    },
    async asyncData(){
      let id = 1;
      let result = await axios.get(url + id);
      return {json_data: result.data};
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
tr th {
  width: 150px;
  background-color: darkblue;
  color: white;
  font-size: 16px;
}
tr td {
  padding: 5px 10px;
  background-color: #eef;
  font-size: 14px;
}
input {
  font-size: 14px;
}
button {
  font-size: 14px;
}
</style>


