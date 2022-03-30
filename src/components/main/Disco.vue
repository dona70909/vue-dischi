<template>
    <div class="card py-1 d-flex flex-column align-items-center justify-content-center">
        <img class="card-img-top" :src="image" alt="Card image cap">
        <div class="card-body p-0 text-center">
            <h5 class="card-title">{{title}}</h5>
            <p  class="card-text m-0">{{author}}</p>
            <p class="m-0">{{year}}</p>
        </div>
    </div>
</template>

<script>
export default {
    name:"DiscoMain",

    props:{
        /* "nomeprops" : tipoProps */
        "image":String,
        "title":String,
        "author":String,
        "year":String
    }
}
</script>

<style lang="scss" scoped>
.card{
    width: calc(70% / 5);

    img{
        width: 80%;
    }
}
</style>