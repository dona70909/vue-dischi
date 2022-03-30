<template>
    <div class="card py-2 d-flex flex-column align-items-center justify-content-center">
        <img class="card-img-top" :src="image" alt="Card image cap">
        <div class="card-body p-0 text-center">
            <h5 class="card-title text-white fw-bolder text-uppercase">{{title}}</h5>
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
@import "@/assets/scss/style.scss";

.card{
    width: calc(80% / 5);
    background:$lightGrey;

    img{
        width: 80%;
        margin-bottom: .5rem;
    }

    .card-body{

        h5{
            font-size: .9rem;
        }
        p{
            color:$greyTextColor;
            font-size: .8rem;
            font-weight: 600;
        }
    }

}
</style>