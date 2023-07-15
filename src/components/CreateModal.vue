<template>
    <div class="modal fade" tabindex="-1" ref="modal">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title">Create New Product</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <!-- Input fields for creating a new product -->
                    <div class="mb-3">
                        <label for="productName" class="form-label">Product Name</label>
                        <input type="text" id="productName" class="form-control" v-model="name" />
                    </div>
                    <div class="mb-3">
                        <label for="productPrice" class="form-label">Price</label>
                        <input type="number" id="productPrice" class="form-control" v-model="price" />
                    </div>
                    <div class="mb-3">
                        <label for="productDetail" class="form-label">Detail</label>
                        <textarea id="productDetail" class="form-control" rows="4" v-model="detail"></textarea>
                    </div>
                </div>
                <div class="modal-footer">
                    <button @click="createProduct" class="btn btn-primary">Save</button>
                    <button @click="closeCreateModal" type="button" class="btn btn-secondary"
                        data-bs-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
</template>
  
<script>
import axios from "axios";

export default {
    data() {
        return {
            name: "",
            price: 0,
            detail: "",
        };
    },

    methods: {
        async createProduct() {
            try {
                // Create a new product object with the input data
                const newProduct = {
                    name: this.name,
                    price: this.price,
                    detail: this.detail,
                };

                // Make the POST request to create the product
                const response = await axios.post("http://localhost:8080/api/v1/products", newProduct, {
                    headers: { Authorization: `Bearer ${localStorage.getItem("access_token")}` },
                });

                // Emit the "created" event to notify the parent component (DataTable)
                this.$emit("created", response.data);

                // Close the modal
                this.closeModal();
            } catch (error) {
                console.error("Error creating product:", error);
            }
        },

        closeModal() {
            const modal = new bootstrap.Modal(this.$refs.modal);
            modal.hide();
        },

        closeCreateModal() {
            // Close the modal when the "Close" button is clicked
            this.closeModal();
        },
    },
};
</script>
  
<style>
/* You can add custom styles for the modal if needed */
</style>
  