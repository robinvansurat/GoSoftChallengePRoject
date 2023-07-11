<script setup>
import banner from "../assets/image 2.png"
</script>

<template>
    <div class="banner">
        <!-- Content inside the banner -->
        <!-- <h1>Welcome to my website</h1>
            <p>Explore and enjoy!</p> -->
    </div>
    <div class="container-fluid">
        <div class="row">
            <div class="col-12">
                <div class="row">
                    <div class="col-4 text-center mb-4">
                        <img class="tree_item" src="@/assets/image 3.png" />
                    </div>
                    <div class="col-4 text-center">
                        <img class="tree_item" src="@/assets/image 4.png" />
                    </div>
                    <div class="col-4 text-center">
                        <img class="tree_item" src="@/assets/image 5.png" />
                    </div>
                </div>
            </div>

        </div>
    </div>
    <div class="banner2">
        <!-- Content inside the banner -->
        <div class="container row">
            <div class="col-6 row banner2_text">
                <div class="col-12">
                    <p class="banner_text_h1">Stylish joggers are</p>
                </div>
                <div class="col-12">
                    <p class="banner_text_h2">incredibly stretchy</p>
                </div>
                <div class="col-12">
                    <p class="banner_text_h2">for mobility.</p>
                </div>
            </div>
        </div>
    </div>
    <div class="container-fluid">
        <div class="row">
            <div class="col-12">
                <div class="row">
                    <div class="col-4 text-center mb-4">
                        <img class="tree_item" src="@/assets/image 6.png" />
                    </div>
                    <div class="col-4 text-center">
                        <img class="tree_item" src="@/assets/image 7.png" />
                    </div>
                    <div class="col-4 text-center">
                        <img class="tree_item" src="@/assets/image 8.png" />
                    </div>
                </div>
            </div>

        </div>
    </div>
    <!-- <img alt="" class="banner" src="@/assets/image 2.png" /> -->
</template>

<script>
export default {
    name: 'Banner',
};
</script>

<style scoped>
.banner {
    background-image: url('../assets/image 2.png');
    background-size: cover;
    background-position: center;
    width: 100%;
    height: 844px;
    margin: auto;
    /* Set the desired height for your banner */
    color: #fff;
    /* Set the text color */
    /* text-align: center; */
}


.banner2 {
    background-image: url('../assets/res013217d5df99b29a2c943c0c6d3fea85fr 1.png');
    background-size: cover;
    background-position: center;
    width: 100%;
    height: 754px;
    margin: auto;
    /* Set the desired height for your banner */
    color: #fff;
    /* Set the text color */
    /* text-align: center; */
}
.banner_text_h2 {
    font-size: 2.5rem;
}
.banner_text_h1 {
    font-size: 4.5rem;
    font-weight: 600;
}
.banner2_text {
    margin-top: 10%;
    margin-left: 10%;
}

.tree_item {
    margin-top: -15%;
}
</style>


