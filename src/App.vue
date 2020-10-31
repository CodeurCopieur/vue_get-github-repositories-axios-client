<template>
  <div id="app">
    <div class="container">
      <input type="text" v-model="username">
      <button @click="fetchRepos">Click me!</button>

      <ul id="wapper__list-repos">
        <li v-for="repo in repos" :key="repo.name">
          {{ repo.name }}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      username: null,
      repos: null
    }
  },
  methods: {
    fetchRepos() {
      /*
        [1] Get data from api
        [2] Return the response
        [3] Catch error
      */
     return this.$http.get(`https://api.github.com/users/${this.username}/repos`)
            .then( response => {
              this.repos = response.data;
              console.log(this.repos);
            })
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  height: 100vh;
}
</style>
