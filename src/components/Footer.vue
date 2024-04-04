<template>
    <div class="todo-footer">
        <label>
            <input type="checkbox" :checked="isAll" @change="allCheck(isAll)">
            <span>已完成{{count}}/ 全部{{list.length}}</span>
        </label>
        <button @click="clearAll">清除已完成任务</button>
    </div>
</template>

<script lang="ts" name="Footer" setup>
import { defineProps,computed } from 'vue';
const{ list,clearAll}=defineProps(['list','clearAll'])

let count=computed(()=>{
    return list.filter((item: object) => item.done).length;
})
let isAll=computed({
    get(){
        return count.value==list.length&&list.length>0
    },
    set(x){
        console.log(x);
    }
})
function allCheck(isAll){
    if(isAll){
        list.forEach((item:object) => {
        item.done=false
        });
    }
    else{
        list.forEach((item:object) => {
        item.done=true
        });
    }
   
}
</script>
    
<style scoped>
    .todo-footer{
        display: flex;
        justify-content: space-between;
    }
    
</style>