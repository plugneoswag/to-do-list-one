<script setup>
import { ref } from 'vue'

const data = ref({
  textTask:'',
  items: [] ,   
  Elvisible: false,
  
})
 
 function addTask() {
  if (data.value.textTask == ''){
    return;
  }
  data.value.items.push({text: data.value.textTask,
    isDone: false,
    })
  data.value.textTask = '' 
  
  };

  

</script>

<template>
<div class="main"> 
  <div class="input_wrapper"> 
    <input v-model="data.textTask" placeholder="отредактируй меня" class="input">
    <button @click="addTask()">ADD</button>
  </div>




  <div class="task-wraper">

  <div class="task-go">
     <p class="to-do-list">СПИСОК ДЕЛ</p>
 <ul class="task">
    <li :class="{textDelete:item.isDone}" v-for="(item,index) in data.items" :key="item"  >  
        <input type="checkbox" v-model="item.isDone">
        {{item.text}}
        <button v-if="data.Elvisible = item.isDone" class="btnDel" @click="data.items.splice(index, 1)">delete</button>
    </li> 
    
 </ul>
 </div>
 </div>
 </div>

</template>


<style>

.main {          
         /** контенер */   
  margin: 50px auto;
  width: 1500px;

}

.to-do-list{
  
  text-align: center;
}

.to-do-go{
 text-align: center;
}
 

.input_wrapper{
  display: flex;
  margin: 0 auto;
  width: 400px;
}


.input{
  text-align: center;
  width: 100%;
  height: 40px;
}

.task-wraper{
  display: flex;
}

.task{
  color: aqua;
  font-size: 18px;
  list-style-type: none;
}
.btnDel{
  margin-left: 50px;
  background: #3a99ff;
}

.task-go{
  overflow: auto;
  margin: 100px auto;
  border: 1px solid #B25538;
  width: 300px;
}

.textDelete{
  text-decoration: line-through;
}

.task li {
  display: flex;
  justify-content: space-between;
}

</style>
