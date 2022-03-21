<template>
<h3>Добавить задачу</h3>
    <div>
        <form 
          @submit.prevent
          @submit="checkForm"
          class="add__task"
        >          
          <!-- <input 
            v-model.number="task.userId"
            class="input"
            type="text"
            placeholder="Ответственный"> -->
          <p class="error" v-if="errors.length">
              <b>Пожалуйста исправьте указанные ошибки:</b>
               <ul>
                <li v-for="error in errors" :key="error.id">{{ error }}</li>
              </ul>
          </p>

          <input
          v-model="task.title"
            class="input"
            type="text"
            placeholder="Задача"
            
          >    
          <my-button 
            class="btn"
          >+</my-button>
        </form>
    </div>
</template>
<script>
import MyButtom from '@/components/UI/MyButton.vue';

export default {
  emits: ['create'],
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
            },
            errors:[]
        }
    },
    methods:{
        createTask(){
            this.task.id = this.$parent.tasks.length + 1;
            this.task.completed = false
            this.$emit('create', this.task);
               this.task = {
                    userId : '',
                    title : '',
                    completed:''
            }
        },
        checkForm(e){
          if(this.task.title !==""){
            console.log(true);
            this.createTask();
            return true;  
         
          }
            this.errors = [];

          if(this.task.title==""){
            console.log(false)
              this.errors.push('Требуется ввести название задачи.');
          }
        },   
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
  border: 1px solid teal;
  padding: 30px;
  border-radius: 25px;
  position:relative;

}
.error {
  position: absolute;
  top:0px;
  color: red;
}
input{
  margin-right: 10px;
}
</style>