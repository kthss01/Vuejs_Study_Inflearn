<template>
  <nav class="navbar navbar-expand-lg navbar-light bg-light">
    <router-link class="navbar-brand" :to="{ name: 'Home' }">
      Kossie Coder
    </router-link>

    <ul class="navbar-nav mr-auto">
      <li class="nav-item active">
        <router-link class="nav-link" :to="{ name: 'Todos' }">
          Todos
        </router-link>
      </li>
    </ul>
  </nav>
  
  <div class="container">
    <router-view/>
  </div>
  <Toast 
    v-if="showToast" 
    :message="toastMessage"
    :type="toastAlertType"
  />
</template>
 
<script>
import Toast from '@/components/Toast.vue';
import { useToast } from '@/composables/toast';
import { useStore } from 'vuex';

export default {
  components: {
    Toast,
  },
  setup() {
    const store = useStore();
    console.log(store.state.showToast);

    const { 
      showToast,
      toastMessage,
      toastAlertType,
      triggerToast,
    } = useToast();

    return {
      showToast,
      toastMessage,
      toastAlertType,
      triggerToast,
    }
  }
}
</script>
 
<style>

</style>