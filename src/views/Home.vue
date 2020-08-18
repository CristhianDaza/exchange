<template>
  <div>
    <PxAssetsTable :assets="assets" />
  </div>
</template>

<script>
import api from '@/api.js'
import PxAssetsTable from '@/components/PxAssetsTable.vue';

export default {
  name: 'home',
  data() {
    return {
      assets: []
    }
  },
  created() {
    api.getAssets()
      .then(assets => this.assets = assets)
  },
  components: {
    PxAssetsTable
  },
}
</script>