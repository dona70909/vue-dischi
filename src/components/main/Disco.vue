<template>
    <div class="card">
        <img class="card-img-top" :src="image" alt="Card image cap">
        <div class="card-body">
            <h5 class="card-title">{{title}}</h5>
            <p class="card-text">{{author}}</p>
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
    }
}
</script>

<style lang="scss" scoped>
.card{
    width: calc(100% / 5);

    img{
        width: 100%;
    }
}
</style>