<template>
    <header class="container-fluid">
        <div class="row justify-content-between">
            <div class="col-4">
                <div class="container-logo">
                    <img :src="require('@/assets/img/logo-small.png')" alt="logo spotify">
                </div>
            </div>
            <div class="col-4">
                <select v-model="selected" class="form-select">
                    <option class="text-white bg-dark" value=""> All Album </option>
                    <option class="text-white bg-dark" v-for = "(genre,index) in listGenres()" :key="index" :value="genre">{{genre}}</option>
                </select>
            </div>
            <div class="d-none">{{this.giveListParent()}}</div>
            <!-- <div>{{this.giveListParentArtists()}}</div> -->
            <div class="col-4">
                <select v-model="selectedArtsit" class="form-select">
                    <option class="text-white bg-dark" value=""> All Artists </option>
                    <option class="text-white bg-dark" v-for = "(genre,index) in listArtists()" :key="index" :value="genre">{{genre}}</option>
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
            filteredSelectList:[],
        }
    },

    props:{
        "parentList":Array,
    },

    computed: {
        selectedGenres(){
            if(this.selected == ""){
                return this.parentList;
            }else {
                return this.parentList.filter((element) => {
                    return element.genre.includes(this.selected);
                });
            }
        },
        selectedArtsist(){
            if(this.selectedArtsist == ""){
                return this.parentList;
            }else {
                return this.parentList.filter((element) => {
                    return element.author.includes(this.selectedArtsist);
                });
            }
        },
    },

    methods:{
        giveListParent(){
            this.filteredSelectList = this.selectedGenres;
            console.table(this.selectedGenres);
            this.$emit('filterList', this.filteredSelectList)
        }, 

        /*  giveListParentArtists(){
            this.$emit('filterListArtisits', this.selectedArtsist)
        },  */

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