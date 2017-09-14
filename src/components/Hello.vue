<template lang="pug">
  .hello
    p {{ things }}
    h1 {{ msg }}
    h2 Essential Links
    ul
      li
        a(href="https://vuejs.org" target="_blank") Core Docs
      li
        a(href="https://forum.vuejs.org" target="_blank") Forum
      li
        a(href="https://chat.vuejs.org" target="_blank") Community Chat
      li
        a(href="https://twitter.com/vuejs" target="_blank") Twitter
      br
      li
        a(href="http://vuejs-templates.github.io/webpack/" target="_blank") Docs for This Template
    h2 Ecosystem
    ul
      li
        a(href="http://router.vuejs.org/" target="_blank") vue-router
      li
        a(href="http://vuex.vuejs.org/" target="_blank") vuex
      li
        a(href="http://vue-loader.vuejs.org/" target="_blank") vue-loader
      li
        a(href="https://github.com/vuejs/awesome-vue" target="_blank") awesome-vue
</template>

<script>
import Vue from 'vue'
import VueResource from 'vue-resource'
Vue.use(VueResource)

export default {
  name: 'hello',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      things: ''
    }
  },
  created () {
    return this.$http
      .get('http://localhost:3030/query/1?test=true')
      .then(response => response.json())
      .then(response => {
        this.things = response
      })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
