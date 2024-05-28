<script>

export default {
    name: "SingleCard",
    props: ["card"],
}
</script>

<template>
    <div class="col-12 col-sm-5 col-md-3 col-lg-2 mx-md-1 p-0 mb-2">
        <figure class="m-0 h-100">
            <img :src="card.card_images[0].image_url" class="card-img-top img-fluid" alt="">
            <h5 class="card-text my-fs py-2 text-center">{{ card.name }}</h5>
            <h6 class="card-text my-fs py-2s text-center text-dark">{{ card.archetype }}</h6>
        </figure>
    </div>
</template>

<style scoped>
figure {
    background-color: #D48F38;
}
</style>