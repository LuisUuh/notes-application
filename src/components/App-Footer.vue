<template>
  <v-card height="110px">
    <v-footer
      absolute
      padless
    >
      <!-- color="#F5A962" -->
      <v-card
        flat
        color="#3C8DAD"
        tile
        fixed
        width="100%"
        class="lighten-1 text-center"
      >
        <v-card-text>
          <v-btn
            v-for="icon in icons"
            :key="icon"
            class="mx-4"
            icon
          >
            <v-icon size="24px">
              {{ icon }}
            </v-icon>
          </v-btn>
        </v-card-text>

        <v-divider></v-divider>

        <v-card-text class="white--text">
          {{ new Date().getFullYear() }} — <strong><span>💻 whith 🖤 &amp; <a style="text-decoration: none;color: #fff;;" href="">Vue.js</a> </span></strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-card>
</template>
<script>
  export default {
    data: () => ({
      icons: [
        'mdi-home',
        'mdi-email',
        'mdi-calendar',
      ],
    }),

  }
</script>
<style scoped>
    /* background-color: #cfd8dc; */
</style>