<template>
  <div class="flex justify-center items-center h-screen">
    <div class="w-96 bg-white rounded-lg shadow-md p-8">
      <div v-if="!showRegisterForm">
        <h2 class="text-xl font-bold mb-6">Register</h2>
        <form>
          <div class="mb-4">
            <label class="block text-gray-700 font-bold mb-2" for="username">
              Name
            </label>
            <input
              class="appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
              id="username"
              type="text"
              v-model="name"
              placeholder="Enter your name"
            />
          </div>
          <div class="mb-4">
            <label class="block text-gray-700 font-bold mb-2" for="username">
              Email
            </label>
            <input
              class="appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
              id="username"
              type="text"
              v-model="email"
              placeholder="Enter your email"
            />
          </div>
          <div class="mb-6">
            <label class="block text-gray-700 font-bold mb-2" for="password">
              Password
            </label>
            <input
              class="appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
              id="password"
              type="password"
              v-model="password"
              placeholder="Enter your password"
            />
          </div>
          <div class="flex justify-between">
            <button
              class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
              type="button"
              v-on:click="login"
            >
              Sign In
            </button>
            <button
              class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
              type="button"
              @click="showRegisterForm = true"
            >
              New User ?
            </button>
          </div>
        </form>
      </div>

      <div v-if="showRegisterForm" class="mt-8 border-t border-gray-400 pt-8">
        <h2 class="text-xl font-bold mb-6">Login</h2>
        <form>
          <div class="mb-4">
            <label class="block text-gray-700 font-bold mb-2" for="email">
              Email
            </label>
            <input
              class="appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
              id="email"
              type="email"
              placeholder="Enter your email"
            />
          </div>
          <div class="mb-4">
            <label class="block text-gray-700 font-bold mb-2" for="username">
              Username
            </label>
            <input
              class="appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
              id="username"
              type="text"
              placeholder="Enter your username"
            />
          </div>
          <div class="mb-6">
            <label class="block text-gray-700 font-bold mb-2" for="password">
              Password
            </label>
            <input
              class="appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
              id="password"
              type="password"
              placeholder="Enter your password"
            />
          </div>
          <div class="flex justify-between">
            <button
              class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
              type="button"
            >
              Sign Up
            </button>
            <button
              class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline"
              type="button"
              @click="showRegisterForm = false"
            >
              Already a user?
            </button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
const api_base_url = `https://mymeetingsapp.herokuapp.com/api`;
export default {
  name: "Login",

  data() {
    return {
      showRegisterForm: false,
      name: "",
      password: "",
      email: "",
    };
  },
  methods: {
    async login() {
      let data = {
        name: this.name,
        email: this.email,
        password: this.password,
      };

      let response = await fetch(`${api_base_url}/auth/register`, {
        method: "POST",
        headers: {
          "Content-Type": "application/json",
        },
        body: JSON.stringify(data),
      });
      debugger;
      console.log(response);
    },
  },
};
</script>
