<template>
    <div class="container mt-5">
        <div class="mt-3">
            <button @click="toggleCreateForm" class="btn btn-primary">Toggle Create Form</button>
        </div>

        <div v-if="isCreateFormOpen" class="mt-3">
            <div v-if="isCreateFormOpen" class="mt-3">
                <h3>Create New Product</h3>
                <div class="form-group">
                    <label for="name">Name</label>
                    <input type="text" class="form-control" id="name" v-model="newProduct.name" />
                </div>
                <div class="form-group">
                    <label for="price">Price</label>
                    <input type="number" class="form-control" id="price" v-model="newProduct.price" />
                </div>
                <div class="form-group">
                    <label for="detail">Detail</label>
                    <textarea class="form-control" id="detail" v-model="newProduct.detail"></textarea>
                </div>
                <button @click="createProduct" class="btn btn-success mt-2">Create Product</button>
            </div>
        </div>


        <h2>Product DataTable</h2>

        <table class="table table-striped table-hover table-responsive-sm" id="productTable">
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
                            <button @click="openEditModal(product)" class="btn btn-outline-primary me-2">Edit</button>
                            <button @click="confirmDeleteProduct(product)" class="btn btn-danger">Delete</button>
                        </div>
                    </td>
                </tr>
            </tbody>
        </table>
        <edit-modal :product="editedProduct" :show="isModalOpen" @save="saveProduct" @close="isModalOpen = false"
            ref="editModal" />
    </div>
</template>
  
<script>
import axios from "axios";
import EditModal from "@/components/EditModal.vue";

export default {
    data() {
        return {
            products: [],
            editedProduct: {},
            isCreateModalOpen: false,
            isModalOpen: false,
            isCreateFormOpen: false,
            newProduct: {
                name: "",
                price: 0,
                detail: "",
            },
        };
    },
    created() {
        this.fetchProducts();
    },
    methods: {
        initializeDataTable() {
            // Initialize DataTable on the table with the ID 'productTable'
            $(this.$refs.productTable).DataTable();
            let table = new DataTable('#productTable', {
                responsive: true
            });

        },
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
        confirmDeleteProduct(product) {
            const confirmMessage = `Are you sure you want to delete "${product.name}"?`;
            if (confirm(confirmMessage)) {
                this.deleteProduct(product.id);
            }
        },
        async deleteProduct(productId) {
            try {
                const accessToken = localStorage.getItem("access_token");
                await axios.delete(`http://localhost:8080/api/v1/products/${productId}`, {
                    headers: { Authorization: `Bearer ${accessToken}` },
                });

                // If the request is successful, remove the deleted product from the products array.
                this.products = this.products.filter((product) => product.id !== productId);
            } catch (error) {
                console.error("Error deleting product:", error);
            }
        },
        toggleCreateForm() {
            this.isCreateFormOpen = !this.isCreateFormOpen;
        },
        async createProduct() {
            try {
                // Prepare the data for the new product (assuming you have form inputs to gather this data)
                const newProductData = {
                    name: this.newProduct.name,
                    price: this.newProduct.price,
                    detail: this.newProduct.detail,
                };
                const accessToken = localStorage.getItem("access_token");
                const response = await axios.post("http://localhost:8080/api/v1/products", newProductData, {
                    headers: { Authorization: `Bearer ${accessToken}` },
                });
                console.log(response);
                if (response.status === 201) {
                    this.fetchProducts();
                    this.isCreateFormOpen = false;
                    this.newProduct.name = "";
                    this.newProduct.price = 0;
                    this.newProduct.detail = "";
                } else {
                    console.error(response);
                }
            } catch (error) {
                console.error("Error creating product:", error);
            }
        },

    },
    components: {
        EditModal,

    },
};
</script>
  