<template>
  <div class="underlay">
    <h1 class="tasks-title">Add your Tasks</h1>
    <div class="main">
      <input v-model="newTask" type="text" placeholder="Add your tasks"/>
      <button @click="handleClick">+Add</button>
    </div>
    <div class="tasks">
      <Task :tasks="tasks" />
    </div>
  </div>
</template>

<script setup>
import axios from "axios"
import { ref } from 'vue';
import Task from './components/Task.vue';

const newTask = ref('')
const tasks = ref([])

const handleClick = async(e) => {
  e.preventDefault()
  if(newTask.value.trim() !== ''){
    try {
      const res = await axios.post('https://iaadi.mugen.ae/api/doctype/Task1',{
        tasks:newTask.value,status:false
      })
      tasks.value.push(res.data)
      newTask.value=''
    } catch (error) {
      console.error('Error adding task:', error);
    }
  }
}
</script>




<style scoped>
  .underlay{
    background: #282432;
    width:650px;
    min-height: 600px;
    border-radius: 10px;
    display: flex;
    flex-direction: column;
    box-shadow: 0 0 5px rgba(1,1,1,1);
  }
  .tasks {
    margin: .5rem;
    display: flex;
    flex-direction: column;
    justify-content: center;
}
  .main{
    width: 94%;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 1rem;

  }
  .main input{
    width:75%;
    border: none;
    padding: .7rem;
    font-size: 1rem;
    border-radius: 10px;
  }
  .main input:focus{
    outline: none;
    border: 2px solid white;
  }

  button {
  border-radius: 8px;
  border: 1px solid transparent;
  padding: 0.6em 1.2em;
  font-size: 1em;
  font-weight: 500;
  font-family: inherit;
  background-color: #1a1a1a;
  cursor: pointer;
  transition: border-color 0.25s;
}

button:hover {
  border-color: #646cff;
}

button:focus,
button:focus-visible {
  outline: 4px auto -webkit-focus-ring-color;
}
.tasks-title{
  color: red;
}
</style>
