<template>
    <div>
          <form @submit.prevent>
          <h3>Добавить задачу</h3>
          <my-input 
            v-model="task.userId"
            type="text"
            placeholder="Ответственный"
          />
          <my-input 
            v-model="task.title"
            type="text"
            placeholder="Тема задачи"
          />
          <my-button 
            class="btn"
            @click="createTask"
          >Создать задачу</my-button>
        </form>
    </div>
</template>
<script>
import MyInput from '@/components/UI/MyInput.vue';

export default {
  components: { MyInput },
    data(){
        return {
            task: {
                id:'',
                userId:'',
                title:'',
                completed:false
            }
        }
    },
    methods:{
        createTask(){
            this.task.id = (Date.now()).toString().slice(-4,-1);
            this.task.completed = false
            this.$emit('create', this.task)
            this.task = {
                userId : '',
                title : '',
            }
        }
    }
}
</script>
<style>

</style>