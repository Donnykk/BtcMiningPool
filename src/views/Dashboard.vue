<template>
  <div class="p-6 bg-gray-800 min-h-screen text-white">
    <h1 class="text-3xl font-semibold mb-4">Mining Pool Dashboard</h1>

    <div class="grid grid-cols-2 gap-4">
      <div class="p-6 bg-gray-700 rounded-lg shadow">
        <h2 class="text-xl font-bold">Hashrate</h2>
        <p class="text-2xl mt-2">{{ hashrate }} TH/s</p>
      </div>

      <div class="p-6 bg-gray-700 rounded-lg shadow">
        <h2 class="text-xl font-bold">Daily Earnings</h2>
        <p class="text-2xl mt-2">{{ earnings }} BTC</p>
      </div>
    </div>

    <div class="mt-6 p-6 bg-gray-700 rounded-lg shadow">
      <h2 class="text-xl font-bold">Hashrate Trend</h2>
      <LineChart :data="chartData" />
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import LineChart from "@/components/LineChart.vue";

export default {
  components: { LineChart },
  setup() {
    const hashrate = ref(0);
    const earnings = ref(0);
    const chartData = ref([]);

    const fetchStats = async () => {

    };

    onMounted(fetchStats);

    return { hashrate, earnings, chartData };
  },
};
</script>