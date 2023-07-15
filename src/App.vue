<script setup>
</script>

<template>
  <div class="w-100">
    <div class="d-flex ">
      <div class="p-2">
        <RouterLink to="/">Home</RouterLink>
      </div>
      <div class="p-2">
        <RouterLink to="/Products">Products</RouterLink>
      </div>
      <div class="p-2">
        <RouterLink to="/login">Login</RouterLink>
      </div>
      <div class="p-2">
        <RouterLink to="/register">Sign up</RouterLink>
      </div>
      <div class="ml-auto p-2">Flex item</div>
    </div>
  </div>


  <RouterView />
</template>

<style scoped>
</style>
