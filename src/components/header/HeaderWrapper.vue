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
                    <option class="text-white bg-dark" value="">Seleziona </option>
                    <option class="text-white bg-dark" v-for = "(genre,index) in listGenres()" :key="index" :value="genre">{{genre}}</option>
                </select>
            </div>
            <div class="col-4">{{selected}} - {{this.giveListParent()}}</div>
        </div>
    </header>
</template>

<script>


export default {
    name:"HeaderWrapper",
    data(){
        return{
            selected:"",
            genreList:[],
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
    },

    methods:{
        giveListParent(){
            this.filteredSelectList = this.selectedGenres;
            console.table(this.selectedGenres);
            this.$emit('filterList', this.filteredSelectList)
        }, 

        listGenres(){
            this.parentList.forEach(element => {
                if(!this.genreList.includes(element.genre)){
                    this.genreList.push(element.genre);
                }
            });

            return this.genreList;
        }

    },

    mounted(){
        console.error("questa lista e' filtered");
        this.giveListParent();
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