<template>
  <div>
    <button @click="togglePlayback" ref="playButton" class="custom-button">
      <span class="play-icon">Play</span>
    </button>
    <input type="range" v-model="currentYear" min="1965" max="2020" ref="rangeInput" />
    <div id="container"></div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue';
import Highcharts from 'highcharts';

export default {
  setup() {
    const startYear = 1965;
    const endYear = 2020;
    const playButton = ref(null);
    const rangeInput = ref(null);
    const currentYear = ref(startYear);
    let dataset, chart;

    const getData = (year) => {
      const output = Object.entries(dataset).map((country) => {
        const [countryName, countryData] = country;
        return [countryName, Number(countryData[year])];
      });
      return [output[0], output.slice(1, 6)];
    };

    const getSubtitle = () => {
      const totalNumber = getData(currentYear.value)[0][1].toFixed(2);
      return `<span style="font-size: 70px; color: white;line-height: 50px;">${currentYear.value}</span>
          <br>
          <span style="font-size: 23px; color: white">
              Total: <b> ${totalNumber}</b> TWh
          </span>`;
    };

    onMounted(async () => {
      dataset = await fetch(
          'https://cdn.jsdelivr.net/gh/highcharts/highcharts@88f2067/samples/data/nuclear-energy-production.json'
      ).then((response) => response.json());

      chart = Highcharts.chart('container', {
        chart: {
          backgroundColor: 'transparent',
        },
        title: {
          text: null, // 제목을 표시하지 않음
        },
        subtitle: {
          useHTML: true,
          text: getSubtitle(),
          floating: true,
          verticalAlign: 'middle',
          y: 30,
        },

        legend: {
          enabled: false,
        },

        tooltip: {
          valueDecimals: 2,
          valueSuffix: ' TWh',
        },

        plotOptions: {
          series: {
            borderWidth: 0,
            colorByPoint: true,
            type: 'pie',
            size: '100%',
            innerSize: '80%',
            dataLabels: {
              enabled: true,
              crop: false,
              distance: '-10%',
              style: {
                fontWeight: 'bold',
                fontSize: '14px', // 폰트 크기 조절
                color: 'white', // 폰트 색상을 하얀색으로 설정
              },
              connectorWidth: 0,
            },
          },
        },
        colors: ['#69ff00','#00f6ff', '#ff5520', '#ff1f78', '#00b5ff'],
        series: [
          {
            type: 'pie',
            name: startYear,
            data: getData(startYear)[1],
          },
        ],
        credits: {
          enabled: false, // 크레딧(credits) 제거
        },
      });
    });

    const togglePlayback = () => {
      if (chart.sequenceTimer) {
        pause();
      } else {
        play();
      }
    };

    const pause = () => {
      playButton.value.title = 'Play';
      playButton.value.innerText = 'Play';
      clearTimeout(chart.sequenceTimer);
      chart.sequenceTimer = undefined;
    };

    const play = () => {
      playButton.value.title = 'Pause';
      playButton.value.innerText = 'Pause';
      chart.sequenceTimer = setInterval(() => {
        update(1);
      }, 500);
    };

    const update = (increment) => {
      if (increment) {
        currentYear.value = parseInt(currentYear.value, 10) + increment;

      }
      if (currentYear.value > endYear) {
        pause();
      }

      setInterval(() => {
        if(currentYear.value === 2021) {
          currentYear.value = 1965
        }
      }, 5000);


      chart.update(
          {
            subtitle: {
              text: getSubtitle(),
            },
          },
          false,
          false,
          false,

      );

      chart.series[0].update({
        name: currentYear.value,
        data: getData(currentYear.value)[1],
      });
    };

    return { playButton, rangeInput, currentYear, togglePlayback };
  },
};
</script>

<style>
.custom-button {
  background-color: #008CBA; /* 배경 색상 설정 */
  color: #fff; /* 텍스트 색상 설정 */
  border: none;
  border-radius: 4px; /* 버튼 테두리 라운딩 */
  padding: 10px 20px; /* 내용과 버튼 크기 조정 */
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease; /* 호버 효과 애니메이션 */
}

.custom-button:hover {
  background-color: #005f80; /* 호버 시 배경 색상 변경 */
}

.play-icon {
  margin-right: 5px; /* Play 아이콘과 텍스트 사이의 간격 조정 */
}
</style>