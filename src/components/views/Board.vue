<template>
    <section>
        <h3> <span>Mis Paneles</span> -> {{name}} </h3>
        <input type="text" placeholder="Añade una lista" v-model="ListName" @keyup.enter="add()"/>
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
  h3 {
    color: #37474f;
    text-align: left;
    margin: 1.5rem;
    }
    h3 span {
      color: #546e7a;
    }
  section {
    text-align: left;
  }
  .container-board {
    box-sizing: border-box;
    align-items: flex-start;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: flex-start;
  }
  input {
    background-color: #607d8b;
    border: 0;
    border-radius: 3px;
    box-shadow: 0 0 0 0.5px rgba(49,49,93,.03),
      0 2px 5px 0 rgba(49,49,93,.1),
      0 1px 2px 0 rgba(0,0,0,.08);
    color: #607d8b;
    font-size: 1.2rem;
    margin: 0 1rem;
    outline: 0;
    padding: 1rem;
    transition: all 600ms ease;
  }
    input:active,
    input:focus {
      background-color: #fafafa;
    }
    input::placeholder {
      color: #fafafa;
    
  }
</style>