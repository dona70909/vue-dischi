<template>
  <div id="app">
    <HeaderWrapper />
    <!-- ASCOLTO L'EVENTO - QUINDI OTTENGO LA LISTA -->
    <MainWrapper @getList="getListFromChild" />
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
  methods:{
    getListFromChild(element){
      console.warn(element);
    }
  }
}
</script>

<style lang="scss">

</style>
