<template>
     <div v-if="tasks.length > 0" class="reverse">  
          <transition-group name="list">
                <todo-item 
                    v-for="task in tasks" :key="task.id"
                    :task="task"
                    @remove="$emit('remove', task)"
                />        
        </transition-group>  
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
<style >
.reverse{
    display: flex;
    flex-direction: column-reverse;
}
.title__tasks {
    margin-top: 20px;
}

.list-item {
  display: inline-block;
  margin-right: 10px;
}
.list-enter-active, .list-leave-active {
  transition: all 0.4s;
}
.list-enter, .list-leave-to /* .list-leave-active до версии 2.1.8 */ {
  opacity: 0;
  transform: translateX(30px);
}
.list-move {
  transition: transform 0.3s;
}
</style>