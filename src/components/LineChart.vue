<template>
    <div ref="chart" class="w-full h-64"></div>
</template>

<script>
import { ref, onMounted, watch } from "vue";
import * as echarts from "echarts";

export default {
    props: ["data"],
    setup(props) {
        const chart = ref(null);
        let chartInstance = null;

        onMounted(() => {
            chartInstance = echarts.init(chart.value);
            updateChart();
        });

        const updateChart = () => {
            if (!chartInstance || !props.data.length) return;
            chartInstance.setOption({
                xAxis: { type: "category", data: props.data.map((d) => d.time) },
                yAxis: { type: "value" },
                series: [{ data: props.data.map((d) => d.hashrate), type: "line" }],
            });
        };

        watch(() => props.data, updateChart, { deep: true });

        return { chart };
    },
};
</script>