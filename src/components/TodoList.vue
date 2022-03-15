<template>
     <div>
         <h3>Список задач</h3>
         <todo-item 
         v-for="task in tasks" :key="task.id"
         :task="task"
         @remove="$emit('remove', task)"
         />
     </div>
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