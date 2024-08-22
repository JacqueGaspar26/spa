<template>
  <!-- <div id="app">
    <header>
      <h1>{{ title }}</h1>
    </header>
    <main>
      <aside class="sidebar"></aside>
      <div class="content"></div>
    </main>
  </div> -->
  <!-- Aquí esta el header, el titulito -->
  <div id="app">
    <header class="bg-blue-900 text-white">
      <h1 class="text-3xl font-bold p-4 text-center"> {{ title }}</h1>
    </header>
  <!-- Aquí termina el header -->

  <!-- Aquí empieza la barra de navegación -->
    <nav class="bg-pink-700 text-white">
      <ul class="flex justify-left">
        <li class="p-4">
          <router-link to="/">Inicio</router-link>
        </li>
        <li class="p-4">
          <router-link to="/acerca-de">Acerca de</router-link>
        </li>
      </ul>
    </nav>

    <!-- Aquí comienza el main -->
    <main class="flex">
      <aside class="sidebar bg-purple-300 w-1/4 text-start overflow-y: scrollbar;">
        <li class="p-2" v-for="post in posts" :key="post.id">
          <router-link :to="`/post/${post.id}`">
            {{ post.id }} &triangle; {{ post.title }}
          </router-link>
        </li>
      </aside>
      <div class="content w-3/4">
        <router-view></router-view>
      </div>
    </main>

  </div>
</template>

<script>
//import HelloWorld from './components/HelloWorld.vue'
import axios from "axios";
const API_URL = "https://jsonplaceholder.typicode.com";

export default {
  name: 'App',
  data() {
    return {
      title: "Prueba de VUE",
      posts: [],
    };
  },

  components: {
    //     HelloWorld
  },

  methods: {
    getPosts() {
      axios.get(`${API_URL}/posts`).then((response) => {
        this.posts = response.data;
      });
    },
  },
  mounted() {
    this.getPosts();
  },

};
</script>

<!-- <style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style> -->
