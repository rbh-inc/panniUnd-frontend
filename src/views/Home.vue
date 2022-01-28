<template>
  <LandingContent></LandingContent>
  <SectorCategories></SectorCategories>
  <Recommendations></Recommendations>
</template>

<script>
import LandingContent from "../components/LandingContent.vue";
import SectorCategories from "../components/SectorCategories.vue";
import Recommendations from "../components/Recommendation.vue";
export default {
  name: "Home",
  components: {
    SectorCategories,
    LandingContent,
    Recommendations,
  },
};
</script>


