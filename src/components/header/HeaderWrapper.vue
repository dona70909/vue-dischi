<template>
    <header class="container-fluid">
        <div class="row justify-content-between">
            <div class="col-4">
                <div class="container-logo">
                    <img :src="require('@/assets/img/logo-small.png')" alt="logo spotify">
                </div>
            </div>
            <div class="col-4">
                <select v-model="selected" class="form-select" aria-label="Default select example">
                    <!--  <option class="text-white bg-dark" selected>Open this select menu</option> -->
                    <option class="text-white bg-dark" v-for = "(disco,index) in parentList" :key="index" :value="disco.genre">{{disco.genre}}</option>
                </select>
            </div>
            <div class="col-4">{{selected}}</div>
        </div>
    </header>
</template>

<script>


export default {
    name:"HeaderWrapper",
    data(){
        return{
            selected:"Rock",
            selectedGenre:"",
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
            console.log(this.selectedGenres);
            this.$emit('filterList',this.selectedGenres)
        },

        optSel(){
            this.select = this.selectedGenre;
        }
    },

    mounted(){
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