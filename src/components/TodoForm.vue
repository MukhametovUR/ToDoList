<template>
<h3>Добавить задачу</h3>
    <div>
        <form @submit.prevent
          class="add__task"
        >          
          <input 
            v-model.number="task.userId"
            class="input"
            type="text"
            placeholder="Ответственный">
          <input 
          v-model="task.title"
            class="input"
            type="text"
            placeholder="Тема задачи"
          >
          <my-button 
            class="btn"
            @click="createTask"
          >+</my-button>
        </form>
    </div>
</template>
<script>
import MyButtom from '@/components/UI/MyButton.vue'
export default {
  components:{
    MyButtom
  },
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
            this.task.id = Math.floor(Math.random()*20)+10;
            // console.log(this.$emit.tasks)
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
.add__task {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
input{
  margin-right: 10px;
}
</style>