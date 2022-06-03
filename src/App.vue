<template>
  <div id="app">

    <!-- 
      //# @filterList="getListFiltered" custom event created by emit from the header 

      //% passing :parentList="parentDiscList" as props to the child header from mainwrapper
      
      -->
    <HeaderWrapper 
    @filterList="getListFiltered" 
    :parentList="parentDiscList" 
    />
    <!-- 
      //%  @getList="getListFromChild" this a event function from mainWrapper child in order to get the list by axios call get
      // # :filterList="filteGenreList" passing the filter list to the main wrapper
    -->
    <MainWrapper 
    @getList="getListFromChild"
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
      /* creating new data in order to pass props from the child header to mainWrapper child  */
      parentDiscList:[],
      filteGenreList:[],
    
    }
  },

  methods:{

    /* get the list of all the discs by genres from the headerWrapper child */
    getListFromChild(element){
      this.parentDiscList = element;
    }, 

    /* Function that get the disc list filtered by the header component */
    getListFiltered(filtered){
      this.filteGenreList = filtered;
    },


  } 


}
</script>

<style lang="scss">

</style>
