<template>
  <div class="name">
    {{ name }}
    <!-- {{ greeting(name) }} -->
    <!-- {{ greet }} -->
    {{ arr }}
  </div>

  <button 
    class="btn btn-primary"
    v-on:click="updateName"
  >
    Click
  </button>
</template>

<script>
import { ref } from 'vue';
// import { ref, reactive } from 'vue';
export default {
  setup() {
    const name = ref('Kossie Coder1');

    // const arr = reactive({
    //   id: 1
    // });

    const arr = ref({
      id: 1
    })

    // const greeting = (name) => {
    //   return 'Hello, ' + name;
    // };

    // const greet = greeting(name);

    // const consoleLog = () => {
    //   console.log('hello world');
    // };

    const updateName = () => {
      name.value = "Kossie Coder";
      // arr.id = 2;
      arr.value.id = 2; // ref 쓰면
      console.log(name);
    }

    return {
      name,
      arr,
      // greeting,
      // greet,
      // consoleLog,
      updateName,
    };
  }
}
</script>

<style>
  .name {
    color: red;
  }
</style>