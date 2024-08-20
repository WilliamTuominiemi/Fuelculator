<template>
  <div class="max-w-md mx-auto p-6 m-6 bg-white shadow-md rounded-lg">
    <h2 class="text-2xl font-semibold text-gray-800 mb-4">⛽ Fuelculator</h2>
    <h2 class="text-lg font-semibold text-gray-800 mb-4">Trip Cost Planner</h2>

    <div class="mb-4">
      <label for="distance" class="block text-sm font-medium text-gray-700">Route Length (km)</label>
      <input
        v-model="distance"
        type="number"
        min="0"
        class="mt-1 w-full py-2 px-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
      />
    </div>

    <div class="mb-4">
      <label for="fuelEconomy" class="block text-sm font-medium text-gray-700">Fuel Economy (L/100km)</label>
      <input
        id="fuelEconomy"
        v-model="fuelEconomy"
        type="number"
        min="0"
        step=".1"
        class="mt-1 w-full py-2 px-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
      />
    </div>

    <div class="mb-4">
      <label for="fuelPrice" class="block text-sm font-medium text-gray-700">Fuel Price (€/L)</label>
      <input
        id="fuelPrice"
        v-model="fuelPrice"
        type="number"
        min="0"
        step=".1"
        class="mt-1 w-full py-2 px-3 border border-gray-300 rounded-lg focus:outline-none focus:ring-indigo-500 focus:border-indigo-500"
      />
    </div>

    <div class="mt-6">
      <p class="text-lg font-medium text-gray-800">
        Estimated Cost: <span class="text-indigo-600">{{ calculatePrice() }}€</span>
      </p>
    </div>
  </div>
</template>

<script lang="ts">
export default {
  name: 'trip-cost-planner',
  data() {
    return {
      distance: 70,
      fuelEconomy: 4.7,
      fuelPrice: 1.8,
    };
  },
  methods: {
    calculatePrice() {
      return Math.round(this.distance * (this.fuelEconomy / 100) * this.fuelPrice * 100) / 100;
    },
  },
};
</script>

<style scoped>
body {
  font-family: 'Inter', sans-serif;
  background-color: #f9fafb;
}
</style>
