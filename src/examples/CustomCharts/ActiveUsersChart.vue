<template>
  <div class="py-3 mb-3 bg-gradient-dark border-radius-lg pe-1">
    <div class="chart">
      <!-- 그래프 표현하는 부분 -->
      <canvas id="chart-bars" class="chart-canvas" height="170"></canvas>
    </div>
  </div>
  <h6 class="mt-4 mb-0 ms-2">Active Users</h6>
  <p class="text-sm ms-2">
    (<span class="font-weight-bolder">+23%</span>) than last week
  </p>
  <div class="container border-radius-lg">
    <div class="row">
      <div class="py-3 col-3 ps-0">
          <card
            :title="cardStat.card1.title"
            :value="cardStat.card1.value"
            :icon-class="cardStat.card1.iconClass"
            :icon-background="cardStat.card1.iconBackground"
            :progress-width="cardStat.card1.progressWidth"
          >
          </card>
      </div>
      <div class="py-3 col-3 ps-0">
        <card
          :title="cardStat.card2.title"
          :value="cardStat.card2.value"
          :icon-class="cardStat.card2.iconClass"
          :icon-background="cardStat.card2.iconBackground"
          :progress-width="cardStat.card2.progressWidth"
        >
        </card>
      </div>
      <div class="py-3 col-3 ps-0">
        <card
          :title="cardStat.card3.title"
          :value="cardStat.card3.value"
          :icon-class="cardStat.card3.iconClass"
          :icon-background="cardStat.card3.iconBackground"
          :progress-width="cardStat.card3.progressWidth"
          ></card>
      </div>
      <div class="py-3 col-3 ps-0">
        <card
          :title="cardStat.card4.title"
          :value="cardStat.card4.value"
          :icon-class="cardStat.card4.iconClass"
          :icon-background="cardStat.card4.iconBackground"
          :progress-width="cardStat.card4.progressWidth"
        >
        </card>
      </div>
    </div>
  </div>
</template>
<script>
import Chart from "chart.js/auto";

import card from "@/examples/CustomCharts/components/GraphCard.vue";

export default {
  name: "ActiveUsersChart",
  components:{
    card,
  },
  props:{

  },
  data(){
    return {
      cardStat:{
        card1:{
          title:"1월 대비",
          value:"36K",
          iconClass:"fas fa-book",
          iconBackground:"bg-gradient-success",
          progressWidth: "progress-bar bg-dark"
        },
        card2:{
          title:"Clicks",
          value:"2M",
          iconClass:"fas fa-rocket",
          iconBackground:"bg-gradient-warning",
          progressWidth: "progress-bar bg-dark w-90"
        },
        card3:{
          title:"Sales",
          value:"435$",
          iconClass:"fas fa-credit-card",
          iconBackground:"bg-gradient-info",
          progressWidth: "progress-bar bg-dark w-30"
        },
        card4:{
          title:"Items",
          value:"43",
          iconClass:"fas fa-tools",
          iconBackground:"bg-gradient-danger",
          progressWidth: "progress-bar bg-dark w-50"
        }
      }
    }
  },
  mounted() {
    this.cardStat.card1.value = "" + 200-450
    let progressWidthValue = (Math.abs(this.cardStat.card1.value)/450).toFixed(1) * 100
    this.cardStat.card1.progressWidth += " w-" + progressWidthValue
    var ctx = document.getElementById("chart-bars").getContext("2d");
    new Chart(ctx, {
      type: "bar",
      data: {
        labels: ["Apr", "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec"],
        datasets: [
          {
            label: "Sales",
            tension: 0.4,
            borderWidth: 0,
            borderRadius: 4,
            borderSkipped: false,
            backgroundColor: "#fff",
            data: [450, 200, 100, 220, 500, 100, 400, 230, 500],
            maxBarThickness: 6,
          },
        ],
      },
      options: {
        responsive: true,
        maintainAspectRatio: false,
        plugins: {
          legend: {
            display: false,
          },
        },
        interaction: {
          intersect: false,
          mode: "index",
        },
        scales: {
          y: {
            grid: {
              drawBorder: false,
              display: false,
              drawOnChartArea: false,
              drawTicks: false,
            },
            ticks: {
              suggestedMin: 0,
              suggestedMax: 500,
              beginAtZero: true,
              padding: 15,
              font: {
                size: 14,
                family: "Open Sans",
                style: "normal",
                lineHeight: 2,
              },
              color: "#fff",
            },
          },
          x: {
            grid: {
              drawBorder: false,
              display: false,
              drawOnChartArea: false,
              drawTicks: false,
            },
            ticks: {
              display: false,
            },
          },
        },
      },
    });
  },
};
</script>
