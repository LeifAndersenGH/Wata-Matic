<script>
import { Line } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, LineElement, LinearScale, PointElement, CategoryScale} from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, LineElement, LinearScale, PointElement, CategoryScale)
export default {
  name: 'LineChart',
  components: { Line },
  props: {
    chartId: {
      type: String,
      default: 'line-chart'
    },
    datasetIdKey: {
      type: String,
      default: 'label'
    },
    width: {
      type: Number,
      default: 400
    },
    height: {
      type: Number,
      default: 400
    },
    cssClasses: {
      default: '',
      type: String
    },
    styles: {
      type: Object,
      default: () => {}
    },
    plugins: {
      type: Object,
      default: () => {}
    },
    newLabels: {
      type: Array
    }
  },
  data() {
    return {
      chartOptions: {
        scales: {
          y: {
            grace: "1%",
            title: {
              display: true,
              text:'Percentage',
              color: '#FFF'
            },
            beginAtZero: true,
            ticks: {
              color: '#FFF',
              min: 0,
              max: 1,
              stepSize: .1,
              format: {
                style: 'percent'
              }
            },
            grid: {
              color: 'rgba(255,255,255,.2)'
            }
          },
          x:{
            ticks: {
              color: '#FFF'
            },
            grid: {
              color: 'rgba(255,255,255,.2)'
            }
          }
        },
        plugins: {
          legend: {
            display: false,
          }
        },
        responsive: true
      }
    }
  }
}
</script>


<template>
  <Line
    :chart-options="chartOptions"
    :chart-data="chartData"
    :chart-id="chartId"
    :dataset-id-key="datasetIdKey"
    :plugins="plugins"
    :css-classes="cssClasses"
    :styles="styles"
    :width="width"
    :height="height"
  />
</template>