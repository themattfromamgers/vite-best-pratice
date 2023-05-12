<script setup>
import {ref} from 'vue'
defineProps({
    text: String
})

const todoName = ref('')

let todoList = ref([])
const addTodo = ()=>{
    todoList.value.push({
        id: todoList.value.length + 1,
        text: todoName.value
    })
    console.log(todoList)
}

const deleteTodo = (todoItem) => {
  const index = todoList.value.findIndex((todo) => todo.id === todoItem.id);
  if (index !== -1) {
    todoList.value.splice(index, 1);
  }
};

</script>

<template>
    <h1>TODO APP</h1>
    {{ todoName }}
    <input type="text" v-model="todoName">
    <button type="submit" @click="addTodo">Ekle</button>

    <ul>
       <li v-for="i in todoList" :key={i}>{{ i.text }} <button @click="deleteTodo(i)">x</button></li> 
    </ul>
</template>

<style scoped>
</style>