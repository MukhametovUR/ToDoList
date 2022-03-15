<template>
     <div v-if="tasks.length > 0">
         <h3>Список задач</h3>
         <todo-item 
         v-for="task in tasks" :key="task.id"
         :task="task"
         @remove="$emit('remove', task)"
         />
     </div>
     <h2 v-else style="color:red">Список задач пуст</h2>
</template>
<script>
import TodoItem from '@/components/TodoItem.vue';

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

</style>