<template>
    <div class="app">
      <h1> Планировщик задач </h1>
      <div>
        <h3>Добавить задачу</h3>
        <form @click="createTask">
          <input 
          class="input"
          type="text"
          placeholder="Ответственный">
          <input 
          class="input"
          type="text"
          placeholder="Тема задачи">
          <button class="btn">Создать задачу</button>
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
          {userId:1, id:1, title:'Проектирование проекта',completed:false},
          {userId:2, id:2, title:'Создать проект',completed:false},
          {userId:3, id:3, title:'Создать комопненты',completed:false},
          {userId:4, id:4, title:'Сделать декомпозицию',completed:false},
        ],
        title:'',
        body:''
      }
    },
    methods: {

    }
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
