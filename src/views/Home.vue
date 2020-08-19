<template>
  <div>
    <ScaleLoader :loading="isLoading" :color="'#68d391'" />
    <PxAssetsTable v-if="!isLoading" :assets="assets" />
  </div>
</template>

<script>
import api from '@/api.js'
import PxAssetsTable from '@/components/PxAssetsTable.vue';

export default {
  name: 'home',
  data() {
    return {
      assets: [],
      isLoading: false
    }
  },
  created() {
    this.isLoading = true
    api.getAssets()
      .then(assets => this.assets = assets)
      .finally(() => this.isLoading = false)
  },
  components: {
    PxAssetsTable
  },
}
</script>