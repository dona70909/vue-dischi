<template>
  <div id="app">
    <HeaderWrapper :parentList="parentDiscList" />
    <!-- ASCOLTO L'EVENTO - QUINDI OTTENGO LA LISTA -->
    <MainWrapper @getList="getListFromChild"
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
      parentDiscList:null,
    }
  },

  methods:{
    getListFromChild(element){
      console.warn(element);
      this.parentDiscList = element;
      console.table(this.parentDiscList);
    }, 
  }
}
</script>

<style lang="scss">

</style>
