<template>
      <div class="taskList">
            <div> <strong>Задача:</strong> {{ task.id }} </div>
            <div> <strong>Ответственный:</strong> {{ task.userId }} </div>
            <div> <strong>Описание:</strong> {{ task.title }} </div>
            <div> <strong>Статус:</strong> {{ task.completed }} </div>
        </div>
</template>
<script>
export default {
    props : {
        task: {
            type: Object,
            required: true,
        }
    }
}
</script>
<style>
    
</style>