<template>
    <header class="container-fluid">
        <div class="row justify-content-between">
            <div class="col-4">
                <div class="container-logo">
                    <img :src="require('@/assets/img/logo-small.png')" alt="logo spotify">
                </div>
            </div>
            <div class="col-4">
                <select v-model="selected" @change ="$emit('changeSelGenre',selected)" class="form-select">
                    <option class="text-white bg-dark" value=""> All Album </option>
                    <option class="text-white bg-dark" v-for = "(genre,index) in listGenres()" :key="index" :value="genre">{{genre}}</option>
                </select>
            </div>
            <!-- <div class="d-none">{{this.giveListParent()}}</div> -->
            <div class="col-4">
                <select v-model="selectedArtist" @change ="$emit('changeSelArtist',selectedArtist)"  class="form-select">
                    <option class="text-white bg-dark" value=""> All Artists </option>
                    <option class="text-white bg-dark" v-for = "(artist,index) in listArtists()" :key="index" :value="artist">{{artist}}</option>
                </select>
            </div>
        </div>
    </header>
</template>

<script>


export default {
    name:"HeaderWrapper",
    data(){
        return{
            selected:"",
            selectedArtist:"",
            genreList:[],
            artistList:[],
        }
    },

    props:{
        "parentList":Array,
    },


    methods:{
         
        listGenres(){
            this.parentList.forEach(element => {
                if(!this.genreList.includes(element.genre)){
                    this.genreList.push(element.genre);
                }
            });

            return this.genreList;
        },

        listArtists(){
            this.parentList.forEach(element => {
                if(!this.artistList.includes(element.author)){
                    this.artistList.push(element.author);
                }
            });

            return this.artistList;
        }

    },
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