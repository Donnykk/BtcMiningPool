<template>
  <div class="dashboard">
    <!-- 标题 -->
    <h1 class="dashboard-title">Mining Pool Dashboard</h1>

    <!-- 两个统计卡片 -->
    <div class="stats-container">
      <div class="stat-card">
        <h2 class="stat-title">Hashrate</h2>
        <p class="stat-value">{{ hashrate }} TH/s</p>
      </div>
      <div class="stat-card">
        <h2 class="stat-title">Daily Earnings</h2>
        <p class="stat-value">{{ earnings }} BTC</p>
      </div>
    </div>

    <!-- 折线图卡片 -->
    <div class="chart-card">
      <h2 class="chart-title">Hashrate Trend</h2>
      <LineChart :data="chartData" />
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import LineChart from "@/components/LineChart.vue";

export default {
  name: "Dashboard",
  components: {
    LineChart,
  },
  setup() {
    const hashrate = ref(123.45);
    const earnings = ref(0.0123);
    const chartData = ref([
      // 随便模拟一点数据
      { label: "Day1", value: 120 },
      { label: "Day2", value: 130 },
      { label: "Day3", value: 150 },
    ]);

    const fetchStats = async () => {
      // TODO: 在此处异步请求真实数据
      // hashrate.value = ...
      // earnings.value = ...
      // chartData.value = ...
    };

    onMounted(fetchStats);

    return {
      hashrate,
      earnings,
      chartData,
    };
  },
};
</script>

<style scoped>
/* 整个 Dashboard 区域 */
.dashboard {
  /* 背景色、文本色 */
  background-color: #1a202c;
  /* 深灰 */
  color: #fff;

  /* 占满视窗高度，让页面撑满 */
  min-height: 100vh;

  /* 内边距 */
  padding: 2rem;
}

/* Dashboard 标题 */
.dashboard-title {
  font-size: 2rem;
  /* 约等于 32px */
  font-weight: 600;
  margin-bottom: 1rem;
}

/* 统计卡片容器：使用网格布局，也可用 flex 布局 */
.stats-container {
  display: grid;
  grid-template-columns: 1fr 1fr;
  /* 两列 */
  gap: 1.5rem;
  /* 卡片之间的间距 */
  margin-bottom: 2rem;
  /* 与后面内容分开 */
}

/* 单个统计卡片 */
.stat-card {
  background-color: #2d3748;
  /* 次深灰 */
  padding: 1.5rem;
  border-radius: 0.5rem;
  /* 圆角 */
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.25);
}

/* 卡片里的标题 */
.stat-title {
  font-size: 1.25rem;
  /* ~ 20px */
  font-weight: 600;
  margin-bottom: 0.5rem;
}

/* 统计值 */
.stat-value {
  font-size: 1.75rem;
  /* ~ 28px */
  margin-top: 0.5rem;
}

/* 图表卡片 */
.chart-card {
  background-color: #2d3748;
  padding: 1.5rem;
  border-radius: 0.5rem;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.25);
}

/* 图表区域标题 */
.chart-title {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 1rem;
}
</style>