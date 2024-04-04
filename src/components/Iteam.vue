<template>
    <li v-for="(item,index) in list" :key="index">
        <label>
            <input type="checkbox" :checked="item.done" @change="checkTodo(index)">
            <span>{{item.thing}}</span>
        </label>
        <button class='btn' @click="deleteFun(index)">删除</button>
    </li>
</template>
<script lang="ts" name="Item" setup>
    import { defineProps } from 'vue';
    defineProps(['list','deleteFun','checkTodo'])

</script>

<style scoped>
    li{
        list-style: none;
        display: flex;
        justify-content: space-between;
        padding: 5px 15px;
    }
    li:hover .btn{
        display: block;
    }
    .btn{
        display: none;
    }
</style>