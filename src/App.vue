<template>
  <div id="app">
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark justify-content-between">
      <a class="navbar-brand" href="/"><i class="fas fa-fw fa-heart text-danger"></i></a>
      <div id="navbarNavDropdown">
        <div class="ml-auto">
          <a href="./src/assets/VueUsersSrc.zip" class="btn btn-outline-primary">
            <i class="fas fa-fw fa-code"></i>
            Download source
          </a>
        </div>
      </div>
    </nav>
    <main>
      <div class="container">
        <div class="mb-5">
          <h1>{{title}}</h1>
          <h4 class="text-primary">{{sub}}</h4>
          <p>{{text}}</p>
        </div>
        <user-list :users='users'/>
      </div>
    </main>
  </div>
</template>

<script>
import axios from 'axios'
import VueAxios from 'vue-axios'
import UserList from './components/UserList.vue';

const usersSrc = "/src/assets/users.json"; // /users/src live

export default {
  name: 'App',
  data () {
    return {
      title: 'Users in Vue',
      sub: 'A basic user management UI using Bootstrap, Vue and Webpack',
      text: '',
      users: []
    }
  },
  methods: {
    getData(api, dataStore) {
      axios.get(api).then((response) => {
        this[dataStore] = response.data;
      }).catch(error => {
        console.log(error.response)
     });
    }
  },
  created() {
    this.getData(usersSrc, "users");
  },
  components: {
    'user-list': UserList
  }
}

</script>
