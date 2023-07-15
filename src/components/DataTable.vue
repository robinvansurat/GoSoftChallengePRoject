<template>
    <div class="container mt-5">
        <h2>Product DataTable</h2>
        <div class="mb-3">
            <!-- "New" button to open the CreateModal -->
            <button @click="openCreateModal" class="btn btn-primary">New</button>
        </div>
        <table class="table table-striped table-hover table-responsive-sm">
            <thead>
                <tr>
                    <th>ID</th>
                    <th>Name</th>
                    <th>Price</th>
                    <th>Detail</th>
                    <th>Actions</th>
                </tr>
            </thead>
            <tbody>
                <tr v-for="product in products" :key="product.id">
                    <td>{{ product.id }}</td>
                    <td>{{ product.name }}</td>
                    <td>{{ product.price }}</td>
                    <td>{{ product.detail }}</td>
                    <td>
                        <div class="d-flex">
                            <button @click="openEditModal(product)" class="btn btn-outline-primary">Edit</button>
                            <button class="btn btn-danger">Delete</button>
                        </div>
                    </td>
                </tr>
            </tbody>
        </table>



        <!-- Edit Modal -->
        <edit-modal :product="editedProduct" :show="isModalOpen" @save="saveProduct" @close="isModalOpen = false"
            ref="editModal" />
    </div>
</template>
  
<script>
import axios from "axios";
import EditModal from "@/components/EditModal.vue";
import CreateModal from "@/components/CreateModal.vue";

export default {
    data() {
        return {
            products: [],
            editedProduct: {},
            isCreateModalOpen: false,
        };
    },
    created() {
        this.fetchProducts();
    },
    methods: {
        async fetchProducts() {
            try {
                const accessToken = localStorage.getItem("access_token");
                const response = await axios.get("http://localhost:8080/api/v1/products", {
                    headers: { Authorization: `Bearer ${accessToken}` },
                });
                this.products = response.data;
            } catch (error) {
                console.error("Error fetching products:", error);
            }
        },
        openEditModal(product) {
            console.log(product);
            this.editedProduct = { ...product };
            this.isModalOpen = true;
            this.$nextTick(() => {
                const modal = this.$refs.editModal;
                const bootstrapModal = new bootstrap.Modal(modal.$el);
                bootstrapModal.show();
            });
        },
        saveProduct(updatedProduct) {
            // Handle the updated product data received from the EditModal component
            // For this example, we'll update the local products array directly
            const index = this.products.findIndex((p) => p.id === updatedProduct.id);
            if (index !== -1) {
                this.products[index] = updatedProduct;
            }

            // Close the modal
            this.isModalOpen = false;
        },
        openCreateModal() {
            this.isCreateModalOpen = true;
        },

        handleProductCreated(newProduct) {
            // Handle the newly created product data received from the CreateModal component
            // For this example, we'll add the new product to the local products array directly
            this.products.push(newProduct);

            // Close the modal
            this.isCreateModalOpen = false;
        },
    },
    components: {
        EditModal,
        CreateModal,
    },
};
</script>
  