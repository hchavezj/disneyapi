<script setup>
import { onMounted } from 'vue';
// import { ref } from 'vue';
// 
// const count = ref(0)
</script>

<template>
  <div>
    <h1>Hello</h1>
    <card />
  </div>

</template>

<script>
  import card from '@/components/BaseCard.vue';

  export default {
    name: 'Home',
    components: {
      card,
    },
  }
</script>

<style scoped>
</style>
