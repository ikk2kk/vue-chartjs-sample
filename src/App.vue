<template>
  <div class="container">
    <button @click="add">Add 10</button>
    <bar-chart :chartData="barData" :options="barOption"></bar-chart>
  </div>

</template>

<script>

import Bar from './components/Bar.vue'
export default {
  data(){
    return{
      barData: {},
      barOption: {}
    }
  },
  methods: {
    add(){

      let beforeData = this.barData.datasets[0].data[0]

      // これだとグラフに反映されない
      //this.barData.datasets[0].data[0] = beforeData + 10

      // barDataを作り直す
      this.barData = {
        labels: [0],
        datasets: [
          {
            data: [beforeData + 10]
          }
        ]
      }
    },
    drawGraph(){

      // 初期値
      let labels = [0]
      let data = [10]

      // 初期値を設定
      this.barData = {
        labels,
        datasets: [{
          data
        }]
      }
      this.barOption ={
        legend: {
          display: false
        },
        scales: {
          yAxes: [
            {
              ticks: {
                beginAtZero: true,
                max:100
              }
            }
          ]
        }
      }
    }
  },
  name: 'App',
  created(){
    this.drawGraph()
  },
  components: {
    barChart: Bar
  }
}
</script>

<style>

.container{
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
