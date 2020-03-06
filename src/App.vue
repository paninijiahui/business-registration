<template>
  <div id="app">
    <company></company>
    <tab-bar></tab-bar>
  </div>
</template>

<script>
  import Company from './components/tabbar/Company'
  import TabBar from './components/tabbar/TabBar'

  export default {
    name: 'App',
    components: {
      Company,
      TabBar
    }
  }
</script>

<style>
  @import "./assets/css/base.css";
</style>
