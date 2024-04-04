<template>
    <div class="container">
        <Header @send-todo="getList"></Header>
        <List v-bind="{list}"  :deleteFun="deleteFun" :checkTodo="checkTodo"></List>
        <Footer :list="list" :clearAll="clearAll" ></Footer>
    </div>
</template>

<script lang="ts" name="App" setup>
import Header from './components/Header.vue';
import List from './components/List.vue';
import Footer from './components/Footer.vue';
import { reactive,onBeforeMount } from 'vue';
let list=reactive<object[]>([])
function loadData(){
    let allList=localStorage.getItem('todoList')
    if(allList){
        list=reactive(JSON.parse(allList))
    } 
    console.log(list); 
}
function saveData(){
    localStorage.setItem('todoList',JSON.stringify(list))
}
onBeforeMount(()=>{
  loadData()
})
// 添加任务
function getList(val:object){
    list.unshift(val)
    saveData()
}
// 删除任务
function deleteFun(index:number){
    list.splice(index,1)
    saveData()
}
// 任务是否完成
function checkTodo(index:number){
    list[index].done=!list[index].done 
    saveData()
}
// 清除已完成任务
function clearAll(){
    for (let i = list.length - 1; i >= 0; i--) {
        if (list[i].done) {
            list.splice(i, 1);
        }
    }
    saveData()
}
</script>
    
<style>
    .container{
        display: inline-block;
        border: 1px solid #aaa;
        padding: 15px;
    }
</style>