<template>
    <main class="container-fluid">
        <div v-if="disclist != null" class="row py-4 d-flex justify-content-center wrapper-card">
            <Disco v-for = "(disco,index) in filterDiscs"  :key="index.id" 
            :image=disco.poster
            :title=disco.title
            :author=disco.author
            :year=disco.year
            />
        </div>

        <div v-else class="text-white">
            <Loader/>
        </div>
    </main>
</template>

<script>
import Disco from './Disco.vue'
import Loader from './Loader.vue'
import axios from 'axios'

export default {
    name:"MainWrapper",
    components:{
        Disco,
        Loader,
    },
    props:{
        "parentList":Array,
        "filterList":Array,
        "selectedGenre":String,
        "selectedArtist":String
    },

    data(){
        return{
            disclist: [],
        }
    },

    mounted(){
        //setTimeout(this.getDiscListApi,3000);
        this.getDiscListApi();
        console.log(this.selectedGenre)
    },

    computed: {
        filterDiscs(){

            const self = this;
            if(this.selectedGenre === ''){
                return this.disclist;
            }

            return this.disclist.filter(function(el) {
                return el.genre.includes(self.selectedGenre) && el.author.includes(self.selectedArtist)
            })
        }
    },

    methods: {
        getDiscListApi(){
            axios.get('https://flynn.boolean.careers/exercises/api/array/music')
            .then((response) => {
                this.disclist = response.data.response;
                /* PASSO LA LISTA AD APP E POI A HEADER IN ORDER TO GET A SELECTIOABLE OPTIONS FOR GENRES AND ARTISTS  */
                
                console.warn(this.disclist); 
                this.getListToParent();
                return this.disclist;
            })
            .catch((error) => {
                console.error(error);
            })
        },

        getListToParent(){
            this.$emit('getList',this.disclist);
        },

    }
}
</script>

<style lang="scss" scoped>
@import "@/assets/scss/style.scss";

main{
    background:$darkGrey;
    /* display: flex;
    justify-content: center; */
    height: 100vh - 5vh;
    
    
}
.wrapper-card{
    gap: 1rem;
}

</style>