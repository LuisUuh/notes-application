<template>
    <div id="divs">
        <h3>Mis Paneles</h3>
        <div class="boards-collection">
            <span v-if="fetchingData">Cargando...</span>
            <!-- <div> -->
                <input type="text" placeholder="Añade un nuevo panel" v-model="BoardName" @keyup.enter="add()">
            <!-- </div> -->
            <BoardCard v-for="(Board, index) in boards" :key="index" :name="Board.name" :id="Board.id"></BoardCard>
        </div>
    </div>
</template>
<script>
import BoardCard from '@/components/BoardCard'
import { mapState, mapActions } from 'vuex'

export default {
    name: "home-view",
    components: {BoardCard},
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
        }
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
<style >
  h3 {
    text-align: left;
    margin: 1.5rem;
  }
  .boards-collection {
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    padding-top: 1rem;
  }
  input {
    box-sizing: border-box;
    background-color: #546E7A;
    border: 2px solid #546E7A;
    border-radius: 3px;
    font-size: 1.1rem;
    outline: 0;
    padding: 0.5rem;
    transition: all 600ms ease;
    }

    input:focus,
    input:active {
      background-color: white;
      color: #546E7A;
    }
    input::placeholder {
      color: white;
    }
</style>