<template>
    <div class="app">
        <todo-form
          @create="createTask"
        />
        <div class="app__btns">
          <my-select
            v-model="selectedSort"
             :options="sortOptions"
          >
          </my-select>
          </div>
        <todo-list 
          :tasks="tasks"
          @remove="removeTask"
          v-if="!isTaskLoading"
        />
      <div v-else>
        <h2>Идет загрузка........</h2>
        </div>
    </div>
</template>

<script>
import TodoForm from '@/components/TodoForm.vue';
import TodoList from '@/components/TodoList.vue';
import MySelect from '@/components/UI/MySelect.vue';

import axios from 'axios';

  export default {
    components: {
      TodoForm,
      TodoList,
      MySelect
     },
    data() {
      return {
        tasks: [],
        modificatorValue:'',
        isTaskLoading: false,
        selectedSort:'',
        sortOptions: [
            {value:'userId',name:'По исполнителю'},
            {value:'id',name:'По №'},            
            {value:'title',name:'По описанию'},
            {value:'completed',name:'По статусу'}

        ]
      }
    },
    methods: {
      createTask(task){
            this.tasks.push(task)
            },
      removeTask(task){
        this.tasks = this.tasks.filter(p =>p.id !== task.id)
      },
      async fetchTasks(){
        try{
          this.isTaskLoading = true;
                const response = await axios.get('https://jsonplaceholder.typicode.com/todos?_limit=3');
                this.tasks = response.data;
      }catch(e){
          alert('Ошибка')
        }finally{
          this.isTaskLoading = false;
        }
      }
    },
    mounted(){
        this.fetchTasks()
    },

    // computed: {
    //     sortedPost(){
    //     return [...this.tasks].sort((task1, task2) => task1[this.selectedSort]?.localeCompare(task2[this.selectedSort]))
    //     }
    //  }
    // В todo-list нужно передать           :tasks="sortedPost"

    watch: {
        selectedSort(newValue) {
          if(newValue === "title"){
              this.tasks.sort((task1,task2) => {
                  return task1[this.selectedSort]?.localeCompare(task2[this.selectedSort])
          })
          }else{
              this.tasks.sort((a,b) => {
                 return a[this.selectedSort] - b[this.selectedSort]
              })
          }
      }
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
    width: 60%;
    max-width: 50rem;
    margin: 0 auto 6rem;
    position: relative;
}
form {
  display: flex;
  flex-direction: column;
}
.app__btns {
  margin: 15px;
  display: flex;
  justify-content: space-between;
  height: 20px;
}

</style>
