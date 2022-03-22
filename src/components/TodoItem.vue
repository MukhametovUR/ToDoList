<template>
        <div class="task">
            <div>
                <div> <strong>Задача:</strong> {{ task.id }} </div>
                <div> <strong>Ответственный:</strong> {{ task.userId }} </div>
                <div> <strong>Описание:</strong> {{ task.title }} </div>
                <div> <strong>Статус:</strong> {{ task.completed }} </div>
            </div>
            <div class="post__btn">
                <my-button
                    @click="$emit('remove', task)"
                >Удалить</my-button>
            </div>
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
<style scoped>
.task {
    padding: 15px;
    border: 2px solid black;
    margin-top: 15px;
    border-radius: 5px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    
}    
</style>