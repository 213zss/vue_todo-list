<template>
    <div class="todo-header">
        <input type="text" v-model.trim="thing" placeholder="请输入你的任务，按回车键添加" @keydown.enter="addTodo(thing)">
    </div>
</template>
<script lang="ts" name="Header" setup>
    import { ref,defineEmits} from "vue";
    let thing=ref('')
    const emit=defineEmits(['send-todo'])
    function addTodo(val:string){
        if(thing.value){
            thing.value=''
            emit('send-todo',{thing:val,done:false})
        }
        else{
            alert('输入不能为空')
        }
    }
    
</script>

<style scoped>
    .todo-header input{
        width: 400px;
        padding: 10px;
        border-radius: 5px;
        border: 1px solid #ccc;
    }
</style>