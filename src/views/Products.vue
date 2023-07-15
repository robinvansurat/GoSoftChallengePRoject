<template>
    <div class="container">
        <h1>Product DataTable</h1>
        <DataTable />
    </div>
</template>
  
<script>
import DataTable from "../components/DataTable.vue";

export default {
    components: {
        DataTable,
    },
};
</script>
  
<style>
.container {
    margin: 2rem auto;
    max-width: 800px;
}
</style>
  