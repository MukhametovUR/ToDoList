<template>
    <div class="app">
     <todo-form
      @create="createTask"
     />
     <todo-list 
     :tasks="tasks"
     @remove="removeTask"
     />
    </div>
</template>

<script>
import TodoForm from '@/components/TodoForm.vue';
import TodoList from '@/components/TodoList.vue';

  export default {
    components: {
      TodoForm,
      TodoList
    },
    data() {
      return {
        tasks: [
          {id:101, userId:1, title:'Проектирование',completed:false},
          {id:102, userId:2, title:'Создать проект',completed:false},
          {id:103, userId:3, title:'Создать комопненты',completed:false},
          {id:104, userId:4, title:'Сделать декомпозицию',completed:false},
        ]
      }
    },
    methods: {
      createTask(task){
            this.tasks.push(task)
            },
      removeTask(task){
        this.tasks = this.tasks.filter(p =>p.id !== task.id)
      }
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
