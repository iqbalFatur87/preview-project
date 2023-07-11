<template>
  <div class="flex items-center justify-center h-screen">
    <form class="max-w-sm p-6 bg-white shadow-md rounded">
      <h2 class="text-2xl font-bold mb-4">Login</h2>
      <div class="mb-4">
        <label for="username" class="block mb-2">Username</label>
        <input v-model="username" id="username" type="text" class="w-full px-3 py-2 border rounded">
      </div>
      <div class="mb-4">
        <label for="password" class="block mb-2">Password</label>
        <input v-model="password" id="password" type="password" class="w-full px-3 py-2 border rounded">
      </div>
      <button @click="login" class="w-full bg-blue-500 text-white font-bold py-2 px-4 rounded">Login</button>
    </form>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      username: '',
      password: '',
    };
  },
  methods: {
    login() {
      const credentials = {
        username: this.username,
        password: this.password,
      };

      axios
        .post('/api/login', credentials)
        .then((response) => {
          // Simpan token JWT ke local storage atau Vuex
          console.log(response.data.token);
        })
        .catch((error) => {
          // Tangani kesalahan login
          console.error(error);
        });
    },
  },
};
</script>
