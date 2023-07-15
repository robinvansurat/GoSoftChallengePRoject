<template>
  <div class="container mt-5">
    <h2>Login</h2>
    <form @submit.prevent="login">
      <div class="mb-3">
        <label for="email" class="form-label">Email address</label>
        <input v-model="email" type="email" class="form-control" id="email" required>
      </div>
      <div class="mb-3">
        <label for="password" class="form-label">Password</label>
        <input v-model="password" type="password" class="form-control" id="password" required>
      </div>
      <button type="submit" class="btn btn-primary">Login</button>
    </form>
  </div>
</template>
  
<script>
import axios from 'axios';

export default {
  data() {
    return {
      email: "",
      password: "",
    };
  },
  methods: {
    async login() {
      try {
        const response = await axios.post("http://localhost:8080/api/v1/auth/authenticate", {
          email: this.email,
          password: this.password,
        });

        const { access_token, refresh_token } = response.data;

        // Save tokens to local storage
        localStorage.setItem("access_token", access_token);
        localStorage.setItem("refresh_token", refresh_token);

        // Redirect to the dashboard or home page
        // Replace '/dashboard' with the actual path where you want to redirect the user after login
        this.$router.push("/products");
      } catch (error) {
        console.error("Login failed:", error);
        // Handle login error, show an error message, etc.
      }
    },
  },
};
</script>
  