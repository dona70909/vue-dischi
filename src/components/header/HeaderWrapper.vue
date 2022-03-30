<template>
    <header class="container-fluid">
        <div class="row">
            <div class="col-12">
                <div class="container-logo">
                    <img :src="require('@/assets/img/logo-small.png')" alt="logo spotify">
                </div>
            </div>
        </div>
    </header>
</template>

<script>
export default {
    name:"HeaderWrapper"
}
</script>

<style lang="scss" scoped>

header{
    padding: .5rem 3rem;
    background-color: red;

    .container-logo{
        height:5vh;

        img{
            height: 100%;
        }
    }
}

</style>