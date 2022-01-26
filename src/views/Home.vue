<template>
  <LandingContent></LandingContent>
  <SectorCategories></SectorCategories>
</template>

<script>
import LandingContent from "../components/LandingContent.vue";
import SectorCategories from "../components/SectorCategories.vue";
export default {
  name: "Home",
  components: {
    SectorCategories,
    LandingContent,
  },
};
</script>


