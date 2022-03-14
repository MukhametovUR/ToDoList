<template>
    <div>
          <form @submit.prevent>
          <h3>Добавить задачу</h3>
          <input 
            v-model="task.userId"
            class="input"
            type="text"
          placeholder="Ответственный">
          <input 
          v-model="task.title"
            class="input"
            type="text"
            placeholder="Тема задачи"
          >
          <button 
            class="btn"
            @click="createTask"
          >Создать задачу</button>
        </form>
    </div>
</template>
<script>
export default {
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
            this.task.id = Date.now();
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
 .input {
  width: 100%;
  border: 1px solid teal;
  padding: 10px 15px;
  margin-top: 15px;
}
.btn {
  align-self: flex-end;
  margin-top: 15px;
  padding: 10px 15px;
  background: none;
  color: teal;
  border: 1px solid teal;
  border-radius: 5px;
}   
</style>