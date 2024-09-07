<!-- js -->
<script setup>
import { ref } from 'vue';
/**
  todo item
  {
    text: string
    done: boolean (true/false)
  }
 */

const inputValue = ref("");
const todoList = ref([
{ text: 'vue', done: false } ,
{ text: 'react', done: false } ,
{ text: 'vercel', done: false }
]);
const handleClickButton = () => {
  todoList.value.push(inputValue.value);
  console.log("choonsik: " + todoList.value)
};

const handlechange = (event) => {
  const nextValue = event.target.value;
  inputValue.value = nextValue;
};

const handleClickDeleteButton = (index) => {
  todoList.value.splice(index,1);
}
</script>

<template>
  <h4>ToDo List</h4>
  
  <p>메세지: {{ todoList }}</p>
  <!-- <input v-model="inputValue" placeholder="메세지 입력하기" /> -->
  <input v-model="inputValue"/>
x
  <button @click="handleClickButton">확인</button>


  <div class="todo-item" v-for="(item, index) in todoList">
    <input type="checkbox" v-model="item.done" />
    <span :class="{'done-item' : item.done}">
      {{ item.text }}
    </span>
    <button @click="handleClickUpdateButton">수정</button>
    <button @click="handleClickDeleteButton(index)">삭제</button>
  </div>
  <!-- HTML -->
</template>

<!-- CSS -->
<style scoped>
.todo-item {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  border: 1px solid gray;
}

.done-item {
  text-decoration: line-through;
}
</style>
