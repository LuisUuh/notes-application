<template>
    <ul>
        <li v-for="(task, index) in tasks" 
            :key="index" 
            :class="{completed: task.completed}">
            <span @click="markAsCompleted({task})" 
                  class="labelTask">{{task.title}}</span>
            <v-icon @dblclick="deleteTask({taskId: task.id})" class="deleteBox">mdi-delete-forever</v-icon></li>
        <input type="text" placeholder="Add new task" v-model="title" @keyup.enter="add()"/>
    </ul>
</template>
<script>
import { mapActions} from 'vuex'
export default {
    name:'TaskList',
    props:{
        listId: String,
        tasks: Array
    },
    data(){
        return{
            title:''
        }
    },
    methods:{
        ...mapActions([
          'addTask',
          'markAsCompleted',
          'deleteTask'
        ]),
        add(){
            this.addTask({list: this.listId, title: this.title})
            this.title = ''
        }
    }
}
</script>
<style scoped>
.labelTask{
    display: block;
    width: 90%;
    overflow: hidden;
    box-sizing: border-box;
    cursor: pointer;
    padding: 1rem 0 1rem 0;
}
.deleteBox{
  color: rgb(145, 32, 32);
  z-index: 90000;
    position: absolute;
    right: 0;
    top: 10px;
    padding: 5px;
    cursor: pointer;
    }
ul {
  list-style: none;
  margin: 0;
  padding: 0;
}
li {
  position: relative;
  background-color: #fafafa;
  border-radius: 3px;
  border-bottom: 1px solid #ccc;
  margin: 0.25rem 0;
  padding-left: 1rem;
}
.completed {
  background-color: #cfd8dc;
  color: #90a4ae;
  text-decoration: line-through;
}
input {
  box-sizing: border-box;
  background-color: #eceff1;
  border: none;
  border-radius: 3px;
  font-size: 1rem;
  margin: 0.5rem;
  outline: 0;
  padding: 0.75rem 0;
  transition: background-color 600ms ease;
  width: 100%;
}
input:focus,
input:active {
  background-color: #fafafa;
  border-bottom: 1px solid #ccc;
  margin: 0.25rem 0;
  padding: 1rem;
}
input::placeholder {
  color: #90a4ae;
} 
</style>