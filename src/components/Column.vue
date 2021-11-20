<template>
    <section>
        <header>
            <h3>{{name}} <v-icon @dblclick="deleteLists(listId)" class="btn-delete-list">mdi-window-close</v-icon> </h3>
        </header>
        <TaskList :listId="listId" :tasks="tasksList"></TaskList>
    </section>
</template>
<script>
import { mapGetters, mapActions} from 'vuex'
import TaskList from '@/components/TaskList'
export default {
    name: 'Column',
    props:{
        name: String,
        listId: String
    },
    components:{
        TaskList
    },
    computed:{
        ...mapGetters([
            'getTasksFromList'
        ]),
        tasksList(){
            return this.getTasksFromList(this.listId)
        }
    },
    methods:{
        ...mapActions([
            'fetchTasks',
            'deleteList'
        ]),
        deleteLists(listId){
            if (this.tasksList.length === 0) {
                this.deleteList({listId: listId})
            } else {
                alert('You can not delete a list with tasks')
            }
        }
    },
    created(){
        this.fetchTasks({list: this.listId})
    }
}
</script>
<style scoped>
  .btn-delete-list{
      position: absolute;
      top: -8px;
      right: -8px;
      cursor: pointer;
      color: rgb(145, 32, 32);
      text-shadow: 1px 1px 2px #fff, 1px 1px 1px #000;
      opacity: 20%;
      transition: all .3s ease-in-out;
      font-size: 20px;
  }
  .btn-delete-list:hover{
      opacity: 100%;
  }
  section {
    box-sizing: border-box;
    background-color: #eceff1;
    border-radius: 3px;
    box-shadow: 0 0 0 0.5px rgba(49,49,93,.03),
      0 2px 5px 0 rgba(49,49,93,.1),
      0 1px 2px 0 rgba(0,0,0,.08);
    margin: 1rem;
    padding: 1rem;
    width: 30%;
    }
    @media screen and (max-width: 600px) {
        section{
            width: calc(100% - 2rem - 2px);
        }
    }
    @media screen and (min-width: 600px) {
        section{
            width: calc(50% - 2rem - 2px);
        }
    }
    @media screen and (min-width: 1024px) {
        section{
            width: calc(33% - 2rem - 2px);
        }
    }
    @media screen and (min-width: 1200px) {
        section{
            width: calc(25% - 2rem - 2px);
        }
    }
  header {
    color: #37474f;
    margin: 0;
    padding-bottom: 1rem;
  }
  h3 {
    margin: 0;
    position: relative;
  }
</style>