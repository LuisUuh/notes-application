<template>
    <v-app-bar
      app
      dark
      color="#125D98"
      class="txt"
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="../assets/note.png"
          transition="scale-transition"
          width="50"
        />
        <h1>Notes</h1>
      </div>

      <v-spacer></v-spacer>

      <v-btn
        to="/"
        text
      >
        <span class="mr-2">My boards</span>
        <v-icon>mdi-clipboard-list-outline</v-icon>
      </v-btn>
    </v-app-bar>
</template>
<script>
export default {
    name: "App-Header"
}
</script>
<style scoped>
</style>