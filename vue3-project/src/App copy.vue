<!-- 양방향 바인딩 전 수업 내용 -->
<template> <!-- v-bind: == : -->
  <!-- <div v-bind:class="nameClass"> -->
  <div :class="nameClass">
    {{ name }}
    <!-- {{ greeting(name) }} -->
    <!-- {{ greet }} -->
    {{ arr }}
  </div>
  <input v-bind:type="type" v-bind:value="name">
  <button 
    class="btn btn-primary"
    @click="updateName"
  >
   <!--  v-on:click == @click -->
   <!--  v-on:click="updateName" -->
    Click
  </button>
</template>

<script>
import { ref } from 'vue';
// import { ref, reactive } from 'vue';
export default {
  setup() {
    const name = ref('Kossie');
    const type = ref('number');
    const nameClass = ref("");

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
      name.value = "Coder";
      // arr.id = 2;
      arr.value.id = 2; // ref 쓰면
      type.value = "text";
      nameClass.value = "name";
      console.log(name);
    }

    return {
      name,
      arr,
      // greeting,
      // greet,
      // consoleLog,
      updateName,
      type,
      nameClass,
    };
  }
}
</script>

<style>
  .name {
    color: red;
  }
</style>