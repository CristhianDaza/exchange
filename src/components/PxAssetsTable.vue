<template>
  <table>
    <thead>
      <tr class="bg-gray-100 border-b-2 border-gray-400">
        <th></th>
        <th>
          <span>Ranking</span>
        </th>
        <th>Nombre</th>
        <th>Precio</th>
        <th>Cap. de Mercado</th>
        <th>Variación 24hs</th>
        <td class="hidden sm:block"></td>
      </tr>
    </thead>
    <tbody>
      <tr
        v-for="item in assets"
        :key="item.id"
        class="border-b border-gray-200 hover:bg-gray-100 hover:bg-orange-100">
        <td>
          <img
            class="w-6 h-6"
            :src="`https://static.coincap.io/assets/icons/${item.symbol.toLowerCase()}@2x.png`"
            :alt="item.name"
          >
        </td>
        <td>
          <b>#{{item.rank}}</b>
        </td>
        <td>
          <router-link
          class="hover:underline text-green-600"
          :to="{ name: 'coin-detail', params: { id: item.id } }"
          >
            {{item.name}}
          </router-link>
          <small class="ml-1 text-gray-500"> {{item.symbol}} </small>
        </td>
        <td>
          {{item.priceUsd | dollar}}
        </td>
        <td>
          {{item.marketCapUsd | dollar}}
        </td>
        <td
          :class="item.changePercent24Hr.includes('-') ? 'text-red-600' : 'text-green-600'"
        >
          {{item.changePercent24Hr | percent}}
        </td>
        <td class="hidden sm:block">
          <PxButton @click="goToCoin(item.id)">
            <span>Detalle</span>
          </PxButton>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
import PxButton from '@/components/PxButton.vue'

export default {
  name: "PxAssetsTable",

  props: {
    assets: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    goToCoin(id) {
      this.$router.push({ name: 'coin-detail', params: { id } })
    }
  },
  components: {
    PxButton
  }
};
</script>

<style scoped>
.up::before {
  content: "👆";
}

.down::before {
  content: "👇";
}

td {
  padding: 20px 0px;
  font-size: 0.6rem;
  text-align: center;
}

th {
  padding: 5px;
  font-size: 0.6rem;
}

@media (min-width: 640px) {
  td,
  th {
    padding: 20px;
    font-size: 1rem;
  }

  th {
    padding: 12px;
  }
}
</style>
