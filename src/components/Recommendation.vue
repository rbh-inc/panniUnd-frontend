
<template>
  <div id="container">
    <div class="title">
      <h2>Work In Demand / Recommendations</h2>
    </div>
    <div class="cards-section">
      <WorkAdCard></WorkAdCard>
      <WorkAdCard></WorkAdCard>
      <WorkAdCard></WorkAdCard>
      <WorkAdCard></WorkAdCard>
      <WorkAdCard></WorkAdCard>
      <WorkAdCard></WorkAdCard>
      <WorkAdCard></WorkAdCard>
      <WorkAdCard></WorkAdCard>
      <WorkAdCard></WorkAdCard>
      <WorkAdCard></WorkAdCard>
      <WorkAdCard></WorkAdCard>
      <WorkAdCard></WorkAdCard>
      <WorkAdCard></WorkAdCard>
    </div>
  </div>
</template>

<script>
import WorkAdCard from "../components/WorkAdCard.vue";
export default {
  name: "Recommendations",
  components: {
    WorkAdCard,
  },
};
</script>

<style scoped>
#container {
  margin: 20px 5% 0 5%;
}
.title {
  font-family: "Noto Sans", sans-serif;
}
.cards-section {
  font-family: "Poppins", sans-serif;
  margin: 15px 0px;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-content: center;
}
</style>
