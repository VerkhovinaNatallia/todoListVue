<template>
    <div>
      <input class="input" v-model="newTodoText" @keyup.enter="addTodo" placeholder="Add a new task" />
      <ul class="list">
        <li class="item" v-for="todo in todos" :key="todo.id">
          <span :class="{ completed: todo.completed }">{{ todo.text }}</span>
          <div class="blockBtn">
            <button @click="toggleTodoCompletion(todo.id)">Toggle</button>
            <button @click="editTodoPrompt(todo.id)">Edit</button>
            <button @click="deleteTodo(todo.id)">Delete</button>
          </div>
        
        </li>
      </ul>
    </div>
  </template>
  
  <script setup lang="ts">
  import { ref } from 'vue';
  import { useTodoStore } from '../store/todo';
  
  const todoStore = useTodoStore();
  const newTodoText = ref('');
  
  const addTodo = () => {
    if (newTodoText.value.trim()) {
      todoStore.addTodo(newTodoText.value);
      newTodoText.value = '';
    }
  };
  
  const editTodoPrompt = (id: number) => {
    const newText = prompt('Edit task:');
    if (newText !== null) {
      todoStore.editTodo(id, newText);
    }
  };
  
  const { todos, toggleTodoCompletion, deleteTodo } = todoStore;
  </script>
  
  <style scoped>
  div{
    text-align: center;
  }
    input{
        height: 40px;
        width: 70%;
        border: 2px solid #000;
    }
    .list{
        width: 70%;
        margin: 0 auto;
        text-align: left;
        padding: 0;
    }
    .blockBtn{
        display: flex;
        gap: 5px;
    }
    .blockBtn button{
        border: none;
        background-color:rgba(250, 128, 114, 20%);
        
    }
    .item{
        display: flex;
        flex-direction: column;
        gap: 15px;
        margin-top: 20px;
        background: rgba(135, 206, 250, 40%);
    }

  </style>
  