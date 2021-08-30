<template>
  <div id="app">
    <AppHeader></AppHeader>
    <router-view class="container"></router-view>
    <AppFooter></AppFooter>
  </div>
</template>

<script>
import AppHeader from '@/components/App-Header'
import AppFooter from '@/components/App-Footer'
export default {
  name: 'App',
  components:{ AppHeader, AppFooter }
}
</script>

<style>
#app {
  box-sizing: border-box;
  color: #37474f;
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  margin: 0px auto;
  padding: 0;
}
.container{
  /* border: 1px blue solid; */
  padding-bottom: 4rem;
}
body{
  margin: 0;
}

</style>
