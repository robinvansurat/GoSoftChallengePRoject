<script setup>
</script>

<template>
    <div class="banner">
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

            <div class="col-12">
                <div class="text-center mt-5">
                    <p class="txt-new">New Available</p>
                </div>
            </div>

            <div class="col-12">
                <div class="container align-items-center">
                    <div class="row">
                        <div class="col-4 text-center ">
                            <img class="m-3" src="@/assets/image 9.png" />
                        </div>
                        <div class="col-4 text-center">
                            <img class="m-3" src="@/assets/image 10.png" />
                        </div>
                        <div class="col-4 text-center">
                            <img class="m-3" src="@/assets/image 11.png" />
                        </div>
                        <div class="col-4 text-center">
                            <img class="m-3" src="@/assets/image 12.png" />
                        </div>
                        <div class="col-4 text-center">
                            <img class="m-3" src="@/assets/image 13.png" />
                        </div>
                        <div class="col-4 text-center">
                            <img class="m-3" src="@/assets/image 14.png" />
                        </div>
                    </div>

                </div>
            </div>

            <div class="col-12">
                <div class="d-flex justify-content-center mt-5">
                    <a href="/products">
                        <button type="button" class="btn btn-more position-relative">
                            MORE <svg xmlns="http://www.w3.org/2000/svg" width="17" height="27" viewBox="0 0 17 27"
                                fill="none">
                                <path d="M1.56 1.85986L15.14 13.4999L1.56 25.1399" stroke="#79BCCF" stroke-width="3"
                                    stroke-linecap="round" stroke-linejoin="round" />
                            </svg>
                        </button>
                    </a>
                </div>
            </div>

        </div>
    </div>
    <div class="footter">

    </div>
</template>

<script>
// export default {
//     name: 'Banner',
// };
</script>

<style scoped>
.footter {
    width: 1440px;
    height: 216px;
    flex-shrink: 0;
}

.btn-more {

    width: 446.2px;
    height: 97px;
    flex-shrink: 0;

    border-radius: 100px;
    background: #FFF;
    box-shadow: 0px 7px 20px 0px rgba(121, 188, 207, 0.40);

    color: #79BCCF;
    font-family: Montserrat;
    font-size: 40px;
    font-style: normal;
    font-weight: 700;
    line-height: normal;
    letter-spacing: 2px;
    text-transform: uppercase;
}

.txt-new {
    font-size: 8em;
    letter-spacing: 0.3em;
}

.banner {
    background-image: url('../assets/image 2.png');
    background-size: cover;
    background-position: center;
    width: 100%;
    height: 844px;
    margin: auto;
    color: #fff;
}


.banner2 {
    background-image: url('../assets/res013217d5df99b29a2c943c0c6d3fea85fr 1.png');
    background-size: cover;
    background-position: center;
    width: 100%;
    height: 754px;
    margin: auto;
    color: #fff;
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


