<template>
  <div>
    <Navbar/>
    <div class="container">
      <div class="search card card-body">
        <h1>Pesquisar Usuários do GitHub</h1>
        <p class="lead">Digite um nome para encontrar usuários e repositórios</p>
        <input
          @keyup="getUser"
          class="form-control"
          placeholder="Digite o nome de um usuário..."
          required
        >
      </div>

      <div class="row mt-3" v-if="user.length !== 0">
        <div class="col-md-4">
          <Profile :user="user"/>
        </div>
        <div class="col-md-8">
          <Repos v-for="repo in repos" :repo="repo" :key="repo"/>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
import Navbar from "./components/Navbar.vue";
import Profile from "./components/Profile.vue";
import Repos from "./components/Repos.vue";
export default {
  name: "app",
  data() {
    return {
      github: {
        url: "https://api.github.com/users",
        client_id: "",
        client_secret: "",
        sort: "created: asc"
      },
      user: [],
      repos: []
    };
  },
  components: {
    Navbar,
    Profile,
    Repos
  },
  methods: {
    getUser(e) {
      const user = e.target.value;
      const { url, client_id, client_secret, sort } = this.github;
      axios
        .get(
          `${url}/${user}?client_id=${client_id}&client_secret=${client_secret}`
        )
        .then(({ data }) => (this.user = data));

      axios
        .get(
          `${url}/${user}/repos?sort=${sort}&client_id=${client_id}&client_secret=${client_secret}`
        )
        .then(({ data }) => (this.repos = data));
    }
  }
};
</script>