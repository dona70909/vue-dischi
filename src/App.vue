<template>
  <div id="app">
    <HeaderWrapper @filterListArtisits="getListArtistsFiltered" @filterList="getListFiltered" 
    :parentList="parentDiscList" 
    />
    <!-- ASCOLTO L'EVENTO - QUINDI OTTENGO LA LISTA -->
    <MainWrapper @getList="getListFromChild"
    :filterList="filteGenreList"
    :filterArtists="filterArtistList"
    />
  </div>
</template>

<script>
import HeaderWrapper from './components/header/HeaderWrapper.vue'
import MainWrapper from './components/main/MainWrapper.vue'

export default {
  name: 'App',
  components: {
    HeaderWrapper,
    MainWrapper,
  },

  data(){
    return{
      parentDiscList:[],
      filteGenreList:[],
      filterArtistList:[]
    }
  },

  methods:{
    getListFromChild(element){
      this.parentDiscList = element;
      console.log("parentList header")
      console.log(this.parentDiscList);
    }, 

    getListFiltered(filtered){
      this.filteGenreList = filtered;
      console.warn("filter list header")
      console.error(filtered);
      console.warn(this.filteGenreList);
    },

    getListArtistsFiltered(element){
      this.filterArtistList = element;
    }
  } 


}
</script>

<style lang="scss">

</style>
