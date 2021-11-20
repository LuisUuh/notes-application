<template>
      <v-col  cols="12"  sm="12" md="6" lg="3">
        <v-card>
          <v-system-bar style="background-color:#125D98" color="darken-1" dark>
            <v-spacer></v-spacer>
            <!-- <v-icon>mdi-trash-can-outline</v-icon> -->
            <app-modal :id="id" :name="name"/>
          </v-system-bar>
        <!-- card inner -->
          <v-card :to="{name: 'Board', params: {name, id}}"
                  class="mx-auto board-card fx" outlined
                  elevation="2">
          
          <v-list-item three-line>
            <v-list-item-content>
              <v-list-item-title class="text-h5 mb-1 card-text">
                {{ name }}
              </v-list-item-title>
              <v-list-item-subtitle><span class="subtext">Click here to see list</span> <v-icon color="#ffffff80">mdi-cursor-default-click</v-icon></v-list-item-subtitle>
            </v-list-item-content>
              <v-list-item-avatar tile size="50"> <v-icon color="#333">mdi-format-list-text</v-icon> </v-list-item-avatar>
          </v-list-item>
          </v-card>
        </v-card>
      </v-col>
</template>
<script>
import AppModal from './App-Modal.vue'
export default {
  components: { AppModal },
    name: "board-card",
    props:{
        id: String,
        name: String
    }
}
</script>
<style scoped>
.subtext {
  color: #00000090;
  font-size: 11px;
}
  .card-text{
    color:#ddd
  }
  .board-card {
    /* background-color: #3C8DAD; */
    background-color: #F5A962;
    transition: all .3s ease-in-out;
  }

  .board-card:hover {
      background-color: #f3b77f;
      font-weight: bold;
  }
  .fx{
    border-top-left-radius: 0;
    border-top-right-radius: 0;
  }
</style>