<template>
    <header class="container-fluid">
        <div class="row justify-content-between">
            <div class="col-6">
                <div class="container-logo">
                    <img :src="require('@/assets/img/logo-small.png')" alt="logo spotify">
                </div>
            </div>
            <div class="col-6">
                <select class="form-select" aria-label="Default select example">
                    <option class="text-white bg-dark" selected>Open this select menu</option>
                    <option class="text-white bg-dark" v-for = "(disco,index) in parentList" :key="index"  :value="disco.genres">{{disco.genre}}</option> -->
                </select>
            </div>
        </div>
    </header>
</template>

<script>


export default {
    name:"HeaderWrapper",
    props:{
        "parentList":Object,
    }
}
</script>

<style lang="scss" scoped>

header{
    padding: .5rem 3rem;
    background-color: rgb(46, 58, 70);

    .container-logo{
        height:5vh;

        img{
            height: 100%;
        }
    }
}

</style>