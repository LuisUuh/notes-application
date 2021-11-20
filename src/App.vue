<template>
  <v-app>
    <app-header/>
    <v-main class="text">
      <router-view class="container" />
    </v-main>
  <app-footer/>
  </v-app>
</template>

<script>
import AppFooter from './components/App-Footer.vue';
import AppHeader from './components/App-Header.vue';

export default {
  components: { AppHeader, AppFooter },
  name: 'App',
};
</script>
<style>
  /* color: #37474f; */
  .text{
    background: #dddddd;
  }
</style>