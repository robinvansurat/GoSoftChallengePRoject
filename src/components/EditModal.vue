<template>
    <div class="modal" ref="modal" tabindex="-1">
        <div class="modal-dialog">
            <div class="modal-content">
                <div class="modal-header">
                    <h5 class="modal-title">Edit Product {{ editedProduct.name }}</h5>
                    <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
                </div>
                <div class="modal-body">
                    <div class="mb-3">
                        <label for="editName" class="form-label">Name</label>
                        <input v-model="editedProduct.name" type="text" class="form-control" id="editName" required>
                    </div>
                    <div class="mb-3">
                        <label for="editPrice" class="form-label">Price</label>
                        <input v-model="editedProduct.price" type="number" class="form-control" id="editPrice" required>
                    </div>
                    <div class="mb-3">
                        <label for="editDetail" class="form-label">Detail</label>
                        <textarea v-model="editedProduct.detail" class="form-control" id="editDetail" required></textarea>
                    </div>
                </div>
                <div class="modal-footer">
                    <button @click="saveEdit" class="btn btn-primary">Save</button>
                    <button @click="$emit('close')" type="button" class="btn btn-secondary"
                        data-bs-dismiss="modal">Close</button>
                </div>
            </div>
        </div>
    </div>
</template>
  
<script>
import axios from "axios";

export default {
    props: {
        product: {
            type: Object,
            required: true,
        },
    },
    data() {
        return {
            editedProduct: {},
        };
    },
    watch: {
        product: {
            immediate: true,
            deep: true,
            handler(newProduct) {
                // Update the editedProduct when the product prop changes
                this.editedProduct = { ...newProduct };
            },
        },
    },
    methods: {
        async saveEdit() {
            console.log(this.editedProduct);
            try {
                const response = await axios.put(`http://localhost:8080/api/v1/products/${this.editedProduct.id}`, this.editedProduct, {
                    headers: { Authorization: `Bearer ${localStorage.getItem("access_token")}` },
                });
                console.log(response);
                this.$emit("save", response.data);
                console.log("Before closing the modal");
                this.closeModal();
                console.log("After closing the modal");
            } catch (error) {
                console.error("Error updating product:", error);
            }
        },
        closeModal() {
            const modal = new bootstrap.Modal(this.$refs.modal);
            modal.hide();
        },
    },
};
</script>

<style>
.fade-enter-active,
.fade-leave-active {
    transition: opacity 0.3s;
}

.fade-enter,
.fade-leave-to

/* .fade-leave-active in <2.1.8 */
    {
    opacity: 0;
}
</style>