<template>
    <section>
        <h3> <span>My Boards</span> <v-icon>mdi-chevron-double-right</v-icon> {{name}} </h3>
        <div class="ghost">
          <v-tooltip left color="#F5A962">
          <template v-slot:activator="{ on, attrs }">
            <v-icon color="primary"
                    dark
                    v-bind="attrs"
                    v-on="on">mdi-information</v-icon>
          </template>
          <span>* Click to mark as completed</span> <br>
          <span>* Double click to delete task or list</span>
        </v-tooltip>
        </div>
        
        <v-row>
          <v-col cols="12" sm="12" md="6" lg="3">
                          <v-text-field
                              type="text" placeholder="Add new list" 
                              v-model="ListName" @keyup.enter="add()"
                              label="New list"
                              outlined
                              dense
                              color="#125D98"
                          ></v-text-field>
          </v-col>
        </v-row>
        <div class="container-board">
            <Column v-for="(list, index) in boardList" :key="index" :listId="list.id" :name="list.name"></Column>
        </div>
    </section>
</template>
<script>
import Column from '@/components/Column'
import { mapState, mapActions, mapGetters } from 'vuex'
export default {
    name: 'Board-View',
    props:{
        name: String,
        id: String
    },
    components:{
        Column
    },
    data(){
        return{
            ListName:''
        }
    },
    computed:{
      ...mapState([
        'fetchingData'
      ]),
      ...mapGetters([
        'getListsByBoard'
      ]),
      boardList(){
        return this.getListsByBoard(this.id)
      }
    },
    methods:{
      ...mapActions([
        'fetchLists',
        'addColumn'
      ]),
        add(){
            // this.BoardList.push({name: this.ListName})
            this.addColumn({board: this.id, name: this.ListName})
            this.ListName = ''
        }
    },
    created(){
      this.fetchLists({board: this.id})
    }
}
</script>
<style scoped>
.ghost{
  text-align: right;
  position: absolute;
  top: 0;
  right: 0;
  margin: 2em;
  cursor: help;
}
  h3 {
    color: #37474f;
    text-align: left;
    margin: 1.5rem;
    }
    h3 span {
      color: #546e7a;
    }
  .container-board {
    box-sizing: border-box;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    align-items: flex-start;
    justify-content: flex-start;
  }
</style>