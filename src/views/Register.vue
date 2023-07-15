<template>
    <div class="container mt-5">
      <h2>Register</h2>
      <form @submit.prevent="register">
        <div class="mb-3">
          <label for="firstname" class="form-label">First Name</label>
          <input v-model="formData.firstname" type="text" class="form-control" id="firstname" required>
        </div>
        <div class="mb-3">
          <label for="lastname" class="form-label">Last Name</label>
          <input v-model="formData.lastname" type="text" class="form-control" id="lastname" required>
        </div>
        <div class="mb-3">
          <label for="email" class="form-label">Email address</label>
          <input v-model="formData.email" type="email" class="form-control" id="email" required>
        </div>
        <div class="mb-3">
          <label for="password" class="form-label">Password</label>
          <input v-model="formData.password" type="password" class="form-control" id="password" required>
        </div>
        <div class="mb-3">
          <label for="confirmPassword" class="form-label">Confirm Password</label>
          <input v-model="formData.confirmPassword" type="password" class="form-control" id="confirmPassword" required>
        </div>
        <div class="mb-3">
          <label for="role" class="form-label">Role</label>
          <select v-model="formData.role" class="form-select" id="role" required>
            <option value="ADMIN" selected>Admin</option>
          </select>
        </div>
        <button type="submit" class="btn btn-primary">Register</button>
      </form>
    </div>
  </template>
  
  <script>
  import axios from "axios";
  
  export default {
    data() {
      return {
        formData: {
          firstname: "",
          lastname: "",
          email: "",
          password: "",
          confirmPassword: "",
          role: "ADMIN",
        },
      };
    },
    methods: {
      async register() {
        if (this.formData.password !== this.formData.confirmPassword) {
          console.error("Password and Confirm Password do not match.");
          return;
        }
  
        try {
          // Make the registration request to the API endpoint
          const response = await axios.post("http://localhost:8080/api/v1/auth/register", this.formData);
  
          // Handle the response, redirect to login, show a success message, etc.
          console.log("Registration successful:", response.data);
          localStorage.setItem("access_token", response.data.access_token);
        localStorage.setItem("refresh_token", response.data.refresh_token);
          this.$router.push("/products");
        } catch (error) {
          console.error("Registration failed:", error);
          // Handle registration error, show an error message, etc.
        }
      },
    },
  };
  </script>
  