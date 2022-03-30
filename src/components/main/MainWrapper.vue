<template>
    <main class="container-fluid">
        <div class="row p-4 justify-content-center">
            <div class="col-10 d-flex flex-wrap justify-content-center wrapper-card">
                <Disco v-for = "(disco,index) in disclist" :key="index" 
                :image=disco.poster
                :title=disco.title
                :author=disco.author
                />
            </div>
        </div>
    </main>
</template>

<script>
import Disco from './Disco.vue'
import axios from 'axios'

export default {
    name:"MainWrapper",
    components:{
        Disco,
    },

    data(){
        return{
            disclist:null,
        }
    },

    created: function(){
        this.getDiscListApi();
    },

    methods: {
        getDiscListApi(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((response) => {
                this.disclist = response.data.response;
                console.table(response.data.response);
                console.table(this.disclist)
            })
            .catch((error) => {
                console.error(error);
            })
        }
    },
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
   
}

</style>