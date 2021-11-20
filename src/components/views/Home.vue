<template>
    <div>
        <h3 style="color: #125D98">My Boards</h3>
        <div v-if="fetchingData" class="global-spinner">
            <v-progress-circular 
                indeterminate
                color="#F5A962"
                :size="70"
                :width="7">
            </v-progress-circular>
        </div>
        <div style="min-height:50vh;" v-if="!fetchingData">
            <v-container>
                <v-row>
                    <v-col cols="12" sm="12" md="6" lg="3">
                        <v-text-field
                            v-model="BoardName" @keyup.enter="add()"
                            label="New Board"
                            placeholder="Add new board"
                            outlined
                            dense
                            color="#125D98"
                        ></v-text-field>
                    </v-col>
                <BoardCard v-for="(Board, index) in boards" :key="index" :name="Board.name" :id="Board.id"></BoardCard>
                <div v-if="!boards" >
                    <h3 style="color: #125D98">No boards yet</h3>
                </div>
                </v-row>
            </v-container>
        </div>
    </div>
</template>
<script>
import BoardCard from '@/components/BoardCard'
import { mapState, mapActions } from 'vuex'

export default {
    name: "home-view",
    components: {BoardCard, },
    data() {
        return{
            BoardName:'',
        }
    },
    methods:{
        ...mapActions([
            'fetchBoards',
            'addBoard'
        ]),
        add(){
            // this.Boards.push({name: this.BoardName})
            this.addBoard({name: this.BoardName})
            this.BoardName = ''
        },
    },
    computed:{
        ...mapState([
            'boards',
            'fetchingData'
        ]),
    },
    created(){
        this.fetchBoards({user: 1})
    }
}
</script>
<style>
.global-spinner{
    width:100%; 
    min-height:50vh;
    display: flex;
    align-items: center;
    justify-content: center;
}
  h3 {
    text-align: left;
    margin: 1.5rem;
  }
</style>