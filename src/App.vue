<!--
Todo...vue 컴포넌트를 모두 등록할 App.vue
npm run serve
-->
<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput v-on:addTodo="addTodo"></TodoInput>
    <TodoList v-bind:propsdata="todoItems"></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
import { defineComponent } from 'vue';
import TodoHeader from './components/TodoHeader.vue';
import TodoInput from './components/TodoInput.vue';
import TodoList from './components/TodoList.vue';
import TodoFooter from './components/TodoFooter.vue';
//마치 import js와 같은, 단 영역에 무슨 vue

//default면 처음 셋팅?
export default defineComponent({
  data() {
    return {
      todoItems : []
    }
  },
  methods : {
    addTodo(todoItem){
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    }
  }, 
  created(){
    if (localStorage.length > 0){
      for(var i=0;i<localStorage.length;i++){
          this.todoItems.push(localStorage.key(i));
      }
    }  
  },  
  components : {
    //영역에 무슨 vue, 무슨 div
    'TodoHeader' : TodoHeader,
    'TodoInput' : TodoInput,
    'TodoList' : TodoList,
    'TodoFooter' : TodoFooter
  }
})
</script>

<style>
  body {
    text-align: center;
    background-color: #F6F6F8;;
  }
  input {
    border-style :groove;
    width:200px;
  }
  button {
    border-style :groove;
  }
  .shadow {
    box-shadow : 5px 10px 10px rgba(0, 0, 0, 0.03)
  }
</style>