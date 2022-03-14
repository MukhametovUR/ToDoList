<template>
    <div class="app">
     <todo-form
      @create="createTask"
     />
     <todo-list 
     :tasks="tasks"
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
          {id:1, userId:1, title:'Проектирование',completed:false},
          {id:2, userId:2, title:'Создать проект',completed:false},
          {id:3, userId:3, title:'Создать комопненты',completed:false},
          {id:4, userId:4, title:'Сделать декомпозицию',completed:false},
        ]
      }
    },
    methods: {
      createTask(task){
            this.tasks.push(task)
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
