<template>
     <div>
         <h3>Список задач</h3>
         <todo-item 
         v-for="task in tasks" :key="task.id"
         :task="task"
         />
     </div>
</template>
<script>
import TodoItem from '@/components/TodoItem.vue'
export default {
  components: {TodoItem  },
    props: {
        tasks: {
            type: Array,
            required: true
        }
    }
}
</script>
<style>
.taskList {
  margin: 10px;
  display: flex;
  border: 1px solid teal;
  flex-direction: column;
  padding: 15px;
  border-radius: 5px;
}    
</style>