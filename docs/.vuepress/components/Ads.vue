<template>
    <div>
      <component :is="selectedAdComponent"></component>
    </div>
  </template>
  
  <script>
  import ArticleAd from './ArticleAd.vue'
  import FakeAds from './FakeAds.vue'
  
  export default {
    name: 'Ads',
    components: {
      ArticleAd,
      FakeAds
    },
    props: {
      probability: {
        type: Number,
        // 此处标记Google广告概率
        default: 0.50
      }
    },
    data() {
      return {
        selectedAdComponent: ''
      }
    },
    created() {
      this.selectAdComponent();
    },
    methods: {
      selectAdComponent() {
        const randomValue = Math.random();
        if (randomValue < this.probability) {
          this.selectedAdComponent = 'ArticleAd';
        } else {
          this.selectedAdComponent = 'FakeAds';
        }
      }
    }
  }
  </script>
  