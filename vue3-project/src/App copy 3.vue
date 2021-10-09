<template>
  <div v-if="toggle">true</div>
  <div v-else>false</div>
  <!-- <div v-show="toggle">true</div>
  <div v-show="!toggle">false</div> -->
  <button @click="onToggle">Toggle</button>

  <div class="container">
    <h1>To-Do List</h1>
    <form 
      class="d-flex"
      @submit.prevent="onSubmit"
    >
      <div class="flew-grow-1 mr-2">
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
    </form>
    <div 
      v-for="todo in todos"
      :key="todo.id"
      class="card mt-2"
    >
      <div class="card-body p-2">
        {{ todo.subject }}
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
export default {
  setup() {
    const toggle = ref(false);
    const todo = ref('');
    const todos = ref([
      {id: 1, subject: '휴대폰 사기'},
      {id: 2, subject: '장보기'},
    ]);

    const onSubmit = () => {
      // e.preventDefault();
      // console.log(todo.value);
      todos.value.push({
        id: Date.now(), // unique 하기 위해서 현재시간을 넣음
        subject: todo.value,
      });
    };

    const onToggle = () => {
      toggle.value = !toggle.value;
    }

    return {
      todo,
      todos,
      onSubmit,
      toggle,
      onToggle,
    };
  }
}
</script>

<style>
  .name {
    color: red;
  }
</style>