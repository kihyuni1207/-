<template>
  <div class="chart-container">
    <div class="chart" id="chart1"></div>
  </div>
</template>

<script>
import {ref, onMounted} from 'vue';
import Highcharts from 'highcharts';


export default {
  setup() {
    const chart1 = ref(null);

    // Sample data for the charts
    const data1 = Array.from({length: 5}, () => Math.floor(Math.random() * 100));
    const data2 = Array.from({length: 5}, () => Math.floor(Math.random() * 100));
    const data3 = Array.from({length: 5}, () => Math.floor(Math.random() * 100));
    const data4 = Array.from({length: 5}, () => Math.floor(Math.random() * 100));

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



    onMounted(() => {
      // Chart 1 configuration
      chart1.value = Highcharts.chart('chart1', {
        chart: {
          backgroundColor: 'transparent', // 차트 백그라운드 색상을 투명으로 설정
        },
        title: {
          text: null, // 상단 차트 제목을 제거
        },
        xAxis: {
          visible: false, // X 축을 숨김
        },
        yAxis: {
          title: {
            text: null, // 왼쪽 Y 축의 타이틀을 제거
          },
          labels: {
            style: {
              color: '#fff',
            },
          },
          gridLineWidth: 0, // 가로선 제거
          max: 100, // Y 축 최대 값 설정
        },
        legend: {
          enabled: false,
        },
        tooltip: {
          shared: true,
          backgroundColor: 'rgba(38,38,38,0.7)', // 툴팁 배경색을 설정
          borderColor: 'transparent', // 툴팁 테두리를 숨김
          headerFormat: '', // 툴팁 헤더 형식을 빈 문자열로 설정하여 인덱스를 제거
          formatter: function () {
            // 시리즈별 커스텀 툴팁 정의
            let tooltip = '';
            this.points.forEach((point) => {
              tooltip += '<span style="color: ' + point.series.color + ';">' + point.series.name + ': ' + point.y + '</span><br>';
            });
            return tooltip;
          },
        },
        credits: {
          enabled: false, // 크레딧(credits) 제거
        },
        // Chart configuration as before
        series: [
          {
            name: 'cpu', // 시리즈 이름 설정
            data: data1,
            color: color1,
            marker: {
              symbol: 'circle', // 데이터 포인트의 모양을 원으로 설정
            },
          },
          {
            name: 'memory', // 시리즈 이름 설정
            data: data2,
            color: color2,
            marker: {
              symbol: 'circle', // 데이터 포인트의 모양을 원으로 설정
            },
          },
          {
            name: 'disk', // 시리즈 이름 설정
            data: data3,
            color: color3,
            marker: {
              symbol: 'circle', // 데이터 포인트의 모양을 원으로 설정
            },
          },
          {
            name: 'network', // 시리즈 이름 설정
            data: data4,
            color: color4,
            marker: {
              symbol: 'circle', // 데이터 포인트의 모양을 원으로 설정
            },
          }
        ],
      });
    });

    return {
      chart1,
    };
  },
};
</script>

<style scoped>
.chart-container {
  grid-template-columns: 1fr 1fr; /* Split into two columns */
  gap: 20px; /* Add gap between the rows and columns */
}

.chart {
  width: 100%;
  height: 300px;
  max-width: 100%; /* Limit the maximum width for the charts */
}
</style>
