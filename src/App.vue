<template>
  <HeaderVue />
  <RepresentVue />
  <StatisticVue />
  <BoostVue />
  <FooterVue />
</template>
<script>
import HeaderVue from "./components/Header.vue";
import RepresentVue from "./components/Represent.vue";
import StatisticVue from "./components/Statistic.vue";
import BoostVue from "./components/Boost.vue";
import FooterVue from "./components/Footer.vue";

export default {
  name: "app",
  components: {
    HeaderVue,
    RepresentVue,
    StatisticVue,
    BoostVue,
    FooterVue,
  },
};
</script>
