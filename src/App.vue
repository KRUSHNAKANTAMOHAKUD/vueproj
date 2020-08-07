

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
<script>
import axios from "axios";

export default {
  name: 'app',
  data () {
    return {
      loading: false,
      all_users: null
    }
  },
  mounted () {
    this.loading = true;
    axios
      .get('https://jsonplaceholder.typicode.com/todos')
      .then(response => (this.all_users = response.data))
      .catch(error => console.log(error))
      .finally(() => this.loading = false)
  }
}
</script>
<template>
  <div id="app" class="container">
    <p v-if="loading">Loading...</p>
    <div v-else>
      <h3 class="heading">Data...</h3>
      <table class="table table-bordered">
        <thead>
          <tr>
            <th scope="col">ID</th>
           <!-- <th scope="col">Avatar</th> -->
            <th scope="col">Title</th>
            <th scope="col">Status</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="user in all_users" v-bind:key="user">
            <td>{{ user.id }}</td>
      
            <td>{{ user.title}}</td>
            <td>{{ user.completed }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>



<style>
#app {
  text-align: center;
  margin-top: 50px;
}
.heading {
  margin-bottom: 30px;
}
</style>
