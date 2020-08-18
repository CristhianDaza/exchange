<template>
  <main>
    <PxHeader />
    <router-view class="container px-5 sm:px-20 py-20 flex justify-center" />
  </main>
</template>

<script>
import PxHeader from '@/components/PxHeader.vue';

export default {
  name: "App",
  components: {
    PxHeader
  },
};
</script>

