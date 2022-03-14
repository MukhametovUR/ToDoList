<template>
        <div class="task">
            <div>
                <div> <strong>Задача:</strong> {{ task.id }} </div>
                <div> <strong>Ответственный:</strong> {{ task.userId }} </div>
                <div> <strong>Описание:</strong> {{ task.title }} </div>
                <div> <strong>Статус:</strong> {{ task.completed }} </div>
            </div>
            <div class="post__btn">
                <my-button class="btn">Удалить</my-button>
            </div>
        </div>        
</template>
<script>
import MyButtom from '@/components/UI/MyButton.vue' 
export default {
    components:{
        MyButtom
    },
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
    border: 2px solid teal;
    margin-top: 15px;
    border-radius: 5px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}    
</style>