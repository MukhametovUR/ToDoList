<template>
    <div class="app">
     <todo-form
      @create="createTask"
     />
     <todo-list 
     :tasks="tasks"
     @remove="removeTask"
     v-if="!isTaskLoading"
     />
     <div v-else><h2>Идет загрузка........</h2></div>
    </div>
</template>

<script>
import TodoForm from '@/components/TodoForm.vue';
import TodoList from '@/components/TodoList.vue';
import axios from 'axios';

  export default {
    components: {
      TodoForm,
      TodoList
    },
    data() {
      return {
        tasks: [],
        modificatorValue:'',
        isTaskLoading: false
      }
    },
    methods: {
      createTask(task){
            this.tasks.push(task)
            },
      removeTask(task){
        this.tasks = this.tasks.filter(p =>p.id !== task.id)
      },
      async fetchTasks(){
        try{
          this.isTaskLoading = true;
                const response = await axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10');
                this.tasks = response.data;
      }catch(e){
          alert('Ошибка')
        }finally{
          this.isTaskLoading = false;
        }
      }
    },
    mounted(){
     this.fetchTasks() 
    }
  
  }
</script>


<style>
/* @import '@/assets/base.css'; */
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 12px;
}
form {
  display: flex;
  flex-direction: column;
}


</style>
