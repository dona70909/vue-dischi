<template>
    <main class="container-fluid">
        <div class="row p-4 justify-content-center">
            <div class="col-10 d-flex flex-wrap justify-content-center wrapper-card">
                <div class="card">
                    <img class="card-img-top" src="https://picsum.photos/200/200.jpg" alt="Card image cap">
                    <div class="card-body">
                        <h5 class="card-title">Card title</h5>
                        <p class="card-text">Some quick example </p>
                    </div>
                </div>

        
                
            </div>
        </div>
    </main>
</template>

<script>
export default {
    name:"MainWrapper",
}
</script>

<style lang="scss" scoped>

main{
    background: rgb(196, 126, 196);
    height: calc(95vh - 1rem);
}
.wrapper-card{
    gap: 1rem;
    background-color: black;
    .card{
        width: calc(100% / 5);

        img{
            width: 100%;
        }
    }
}

</style>