<template>
  <section class="container">
    <h1>{{title}}</h1>
    qqq
    <p>{{$store.state.message}}</p>
    <hr>
    <div class="link"
        @click="$store.dispatch('doit')">
      <a @click.stop="$store.commit('reset')">
        clicked: {{$store.state.counter}}
      </a>
    </div>
    <!-- <router-link to="/sother">Go to Other</router-link> -->
  </section>
</template>

<script>
export default {
  data: function(){
    return {
      title: 'hello',
      message: 'this is message',
    };
  },
};
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
  padding-top: 5px;
  color: #345980;
}
pre {
  padding: 10px;
  font-size: 18px;
  background-color: #efefef;
}
hr {
  margin: 10px 0;
}
a {
  font-size: 16px;
}
.link {
  background-color: #def;
  padding: 10px;
}
</style>
