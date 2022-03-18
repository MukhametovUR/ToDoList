<template>
     <div v-if="tasks.length > 0"
            class="reverse"
         >
         <todo-item 
            v-for="task in tasks" :key="task.id"
            :task="task"
            @remove="$emit('remove', task)"
         />
    <h2 class="title__tasks">Список задач</h2>

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
.reverse{
    display: flex;
    flex-direction: column-reverse;
}
.title__tasks {
    margin-top: 20px;
}
</style>