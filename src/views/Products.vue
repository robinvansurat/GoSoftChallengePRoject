<template>
    <div class="container">
        <div class="row">

            <div class="col-4" v-for="card in cards" :key="card.id">
                <div class="card" style="width: 18rem;">
                    <img :src="card.image" class="card-img-top" :alt="card.title" />
                    <div class="card-body">
                        <h5 class="card-title">{{ card.title }}</h5>
                        <p class="card-text">{{ card.description }}</p>
                        <a href="#" class="btn btn-primary">Go somewhere</a>
                    </div>
                </div>
            </div>

        </div>
    </div>
</template>

<script>
import image1 from '@/assets/image 3.png';
import image2 from '@/assets/image 5.png';

export default {
    name: 'CardList',
    data() {
        return {
            cards: [
                {
                    id: 1,
                    image: image1,
                    title: 'Card 1',
                    description: 'Some quick example text for Card 1',
                },
                {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                },
                {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                }, {
                    id: 2,
                    image: image2,
                    title: 'Card 2',
                    description: 'Some quick example text for Card 2',
                },
            ],
        };
    },
};
</script>



<style scoped></style>