<template>
  <div class="chart-container" style="margin-top:-120px;">
    <div class="chart" id="chart2"></div>
    <div class="chart" id="chart3"></div>
  </div>
</template>


<script>
import {ref, onMounted} from 'vue';
import Highcharts from 'highcharts';

export default {
  setup() {
    const chart2 = ref(null);
    const chart3 = ref(null);

    // Sample data for the second pie chart
    const data1 = Math.floor(Math.random() * 100);
    const data2 = Math.floor(Math.random() * 100);
    const data3 = Math.floor(Math.random() * 100);
    const data4 = Math.floor(Math.random() * 100);
    const data5 = Math.floor(Math.random() * 100);
    const data6 = Math.floor(Math.random() * 100);
    const data7 = Math.floor(Math.random() * 100);
    const data8 = Math.floor(Math.random() * 100);

    function getRandomColor() {
      const letters = '0123456789ABCDEF';
      let color = '#';
      for (let i = 0; i < 6; i++) {
        color += letters[Math.floor(Math.random() * 16)];
      }
      return color;
    }

    const color1 = getRandomColor();
    const color2 = getRandomColor();
    const color3 = getRandomColor();
    const color4 = getRandomColor();


    const color5 = getRandomColor();
    const color6 = getRandomColor();
    const color7 = getRandomColor();
    const color8 = getRandomColor();

    onMounted(() => {
      // Second Pie Chart configuration
      chart2.value = Highcharts.chart('chart2', {
        chart: {
          backgroundColor: 'transparent',
        },
        title: {
          text: null,
        },
        series: [
          {
            type: 'pie', // Set the chart type to 'pie'
            showInLegend: false, // 시리즈 이름을 숨김
            data: [
              {
                y: data1,
                color: color1,
              },
              {
                y: data2,
                color: color2,
              },
              {
                y: data3,
                color: color3,
              },
              {
                y: data4,
                color: color4,
              },
            ],
            dataLabels: {
              enabled: false, // 라벨을 숨김
            },
          },
        ],
        legend: {
          enabled: false,
        },
        tooltip: {
          pointFormat: '<b>{point.percentage:.1f}%</b>',
        },
        credits: {
          enabled: false,
        },
      });
      chart3.value = Highcharts.chart('chart3', {
        chart: {
          backgroundColor: 'transparent',
        },
        title: {
          text: null,
        },
        series: [
          {
            type: 'pie', // Set the chart type to 'pie'
            showInLegend: false, // 시리즈 이름을 숨김
            data: [
              {
                y: data5,
                color: color5,
              },
              {
                y: data6,
                color: color6,
              },
              {
                y: data7,
                color: color7,
              },
              {
                y: data8,
                color: color8,
              },
            ],
            dataLabels: {
              enabled: false, // 라벨을 숨김
            },
          },
        ],
        legend: {
          enabled: false,
        },
        tooltip: {
          pointFormat: '<b>{point.percentage:.1f}%</b>',
        },
        credits: {
          enabled: false,
        },
      });
    });

    return {
      chart2,
    };
  },
};
</script>

<style scoped>
.chart-container {
  display: flex;
  justify-content: space-between; /* 두 차트를 가로로 정렬하고 사이 공간을 균등하게 분배 */
}

.chart {
  width: 50%; /* 각 차트가 컨테이너의 절반 폭을 차지하도록 설정 */
}
</style>
