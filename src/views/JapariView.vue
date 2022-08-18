<template>
<div>
  <h1>자파리용 뷰 이것저것 추가해 보자</h1>
  <div class="py-4 container-fluid">
    <div class="row">
      <div class="col-xl-3 col-sm-6 mb-xl-0 mb-4">
        <card
          :title='cardStat.card.title'
          :title-color='cardStat.card.titleColor'
          :value='cardStat.card.value'
          :value-color="cardStat.card.valueColor"
          :percentage='cardStat.card.percentage'
          :percentage-color="cardStat.card.percentageColor"
          :icon-class='cardStat.card.iconClass'
          :icon-background="cardStat.card.iconBackground"
          :content-class="cardStat.card.contentClass"
          :direction-revers="cardStat.card.directionReverse"
        >
        </card>
      </div>
      <div class="col-xl-3 col-sm-6 mb-xl-0 mb-4">
        <default-info-card
          :icon-bg="cardStat.defaultInfoCard.iconBg"
          :class-icon="cardStat.defaultInfoCard.classIcon"
          :title="cardStat.defaultInfoCard.title"
          :desc="cardStat.defaultInfoCard.desc"
          :price="cardStat.defaultInfoCard.price"
        ></default-info-card>
      </div>
      <div class="col-xl-3 col-sm-6 mb-xl-0 mb-4">
        <master-card></master-card>
      </div>
      <div class="col-xl-3 col-sm-6 mb-xl-0 mb-4">
        <card
          :title='cardStat.card.title'
          :title-color='cardStat.card.titleColor'
          :value='cardStat.card.value'
          :value-color="cardStat.card.valueColor"
          :percentage='cardStat.card.percentage'
          :percentage-color="cardStat.card.percentageColor"
          :icon-class='cardStat.card.iconClass'
          :icon-background="cardStat.card.iconBackground"
          :content-class="cardStat.card.contentClass"
          :direction-revers="cardStat.card.directionReverse"
        >
        </card>
      </div>
    </div>
  </div>
  <div class="mt-4 row">
    <div class="mb-4 col-lg-12 mb-lg-0">
      <div class="card z-index-2">
        <div class="p-3 card-body">
          <!-- chart -->
          <active-users-chart />
        </div>
      </div>
    </div>
  </div>
  <div class="mt4 row">
    <div class="mb-4 col-lg-12 mb-lg-0">
      <div class="card z-index-2">
        <div class="p-3 card-body">
          <!-- chart -->
          <gradient-line-chart />
        </div>
      </div>
    </div>
  </div>
</div>
</template>

<script>
//card 자파리
import card from "@/examples/Cards/Card.vue";
import defaultInfoCard from "@/examples/Cards/defaultInfoCard.vue";
import masterCard from "@/examples/Cards/masterCard.vue"

//chart 자파리
import activeUsersChart from "@/examples/CustomCharts/ActiveUsersChart.vue";
import gradientLineChart from "@/examples/CustomCharts/GradientLineChart.vue";

export default {
  name: "JapariView",
  components:{
    card,
    defaultInfoCard,
    masterCard,
    activeUsersChart,
    gradientLineChart,
  },
  data(){
    return {
      cardStat:{
        card:{
          title: "타이틀",
          titleColor: "bg-gradient-success",
          value: "값 영업을 늘립니다.",
          valueColor: "bg-gradient-warning",
          percentage: "퍼센트 영역을 늘립니다.",
          percentageColor: "bg-gradient-danger",
          iconClass: "fas fa-coins",
          directionReverse: true,
          iconBackground: "bg-gradient-success",
        },
        defaultInfoCard:{
          iconBg: "bg-danger",
          classIcon: "far fa-address-book",
          title: "어드레스 북",
          desc: "디스크립션",
          price: "프라이스",
        }
      }
    }
  }
};
</script>

<style scoped>

</style>