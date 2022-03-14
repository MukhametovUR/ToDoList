<template>
    <div class="app">
      <h1> Планировщик задач </h1>
      <div>
        <h3>Добавить задачу</h3>
        <form 
        @submit.prevent>
          <input 
            v-bind:value="userId"
            @input="userId = $event.target.value"
            class="input"
            type="text"
          placeholder="Ответственный">
          <input 
            v-bind:value="title"
            @input="title = $event.target.value"
            class="input"
            type="text"
            placeholder="Тема задачи"
          >
          <button 
            class="btn"
            @click="createTodo"
          >Создать задачу</button>
        </form>
        <div 
        v-for="item in tasks" :key="item.id"
        class="taskList">
          <div> Задача: {{ item.id }} </div>
          <div> Ответственный: {{ item.userId }} </div>
          <div> Описание: {{ item.title }} </div>
          <div> Статус: {{ item.completed }} </div>
        </div>
      </div>
    </div>
</template>

<script>
  export default {
    data() {
      return {
        tasks: [
          {id:1, userId:1, title:'Проектирование проекта',completed:false},
          {id:2, userId:2, title:'Создать проект',completed:false},
          {id:3, userId:3, title:'Создать комопненты',completed:false},
          {id:4, userId:4, title:'Сделать декомпозицию',completed:false},
        ],
        userId:'',
        title:''
      }
    },
    methods: {
        createTodo(){
          const newTodo = {
            id: this.tasks.length + 1,
            userId: this.userId, 
            title: this.title, 
            completed:false
          }
          this.tasks.push(newTodo);
          this.userId= '',
          this.title= ''
        }
    },
  
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
.taskList {
  margin: 10px;
  display: flex;
  border: 1px solid teal;
  flex-direction: column;
  padding: 15px;
  border-radius: 5px;
}
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
