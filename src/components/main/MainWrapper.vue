<template>
    <main class="container-fluid">
        <div class="row justify-content-center">
            <div class="col-8 d-flex flex-wrap justify-content-center wrapper-card">
                <Disco v-for = "(disco,index) in disclist" :key="index" 
                :image=disco.poster
                :title=disco.title
                :author=disco.author
                :year=disco.year
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
        return setTimeout(this.getDiscListApi(),10000);
        /* this.getDiscListApi(); */
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
    background: rgb(30, 45, 59);
    height: calc(95vh - 1rem);
    display: flex;
    justify-content: center;
    align-items: center;
}
.wrapper-card{
    gap: 1rem;
}

</style>