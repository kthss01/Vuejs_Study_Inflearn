<template>
  <div class="container">
    <h1>To-Do List</h1>
    <form @submit.prevent="onSubmit">
    <div class="d-flex">
      <div class="flex-grow-1 mr-2">
        <input 
          class="form-control"
          type="text" 
          v-model="todo"
          placeholder="Type new to-do"
        >
      </div>
      <div>
        <button 
          class="btn btn-primary"
          type="submit"
        >
          Add
        </button>
      </div>
    </div>
    <div v-show="hasError" style="color: red">
      This field cannot be empty
    </div>
    </form>
    <div v-if="!todos.length">
      추가된 Todo가 없습니다
    </div>
    <div 
      v-for="(todo, index) in todos"
      :key="todo.id"
      class="card mt-2"
    >
      <div class="card-body p-2 d-flex align-items-center">
        <div class="form-check flex-grow-1">
          <input 
            class="form-check-input" 
            type="checkbox"
            v-model="todo.completed"
          >
          <label 
            class="form-check-label" 
            :class="{ todo: todo.completed }"
          >
          <!-- <label 
            class="form-check-label" 
            :style="todo.completed ? todoStyle : {}"
          > -->
            {{ todo.subject }}
          </label>
        </div>
        <div>
          <button 
            class="btn btn-danger btn-sm"
            @click="deleteTodo(index)"
          >
            Delete
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
export default {
  setup() {
    const todo = ref('');
    const todos = ref([]);
    const hasError = ref(false);
    const todoStyle = {
      textDecoration: 'line-through',
      color: 'gray',
    }

    const onSubmit = () => {
      if (todo.value === '') {
        hasError.value = true;
      } else {
        todos.value.push({
          id: Date.now(), // unique 하기 위해서 현재시간을 넣음
          subject: todo.value,
          completed: false,
        });
        hasError.value = false;
        todo.value = "";
      }
    };

    const deleteTodo = (index) => {
      todos.value.splice(index, 1);
    };

    return {
      todo,
      todos,
      onSubmit,
      hasError,
      todoStyle,
      deleteTodo,
    };
  }
}
</script>

<style>
  .todo {
    color: gray;
    text-decoration: line-through;
  }
</style>