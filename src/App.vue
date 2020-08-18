<template>
  <main>
    <PxHeader />
    <PxAssetsTable />
  </main>
</template>

<script>
import PxHeader from '@/components/PxHeader.vue';
import PxAssetsTable from '@/components/PxAssetsTable.vue';

export default {
  name: "App",
  components: {
    PxHeader,
    PxAssetsTable
  },
};
</script>

