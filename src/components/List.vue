<template>
    <ul class="todo-List">
        <Iteam v-bind="$attrs" :deleteFun="deleteFun" :checkTodo="checkTodo"></Iteam>
    </ul>
</template>
<script lang="ts" name='List' setup>
    import Iteam from "./Iteam.vue";
    import {defineProps} from 'vue'
    defineProps(['deleteFun','checkTodo'])
</script>
    
<style scoped>
    .todo-List{
        border: 1px solid #ddd;
        padding: 0;
    }
    .todo-List li{
        list-style: none;
        display: flex;    
        justify-content: space-between;
        align-items: center;
        padding: 0 5px;
        border-bottom: 1px solid #ddd;
        height: 35px;
    }
    .todo-List li:hover{
        background-color: #ccc;
    }
    
</style>