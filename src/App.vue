<template>
  <div id="app">
    <HeaderWrapper @filterList="getListFiltered" :parentList="parentDiscList" />
    <!-- ASCOLTO L'EVENTO - QUINDI OTTENGO LA LISTA -->
    <MainWrapper @getList="getListFromChild"
    :filterList="filteGenreList"
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
    }
  },

  methods:{
    getListFromChild(element){
      this.parentDiscList = element;
      console.warn(this.parentDiscList);
    }, 

    getListFiltered(filtered){
      this.filteGenreList = filtered;
      console.log("filter")
      console.warn(this.filteGenreList);
    }
  } 


}
</script>

<style lang="scss">

</style>
