<template>
  <div class="container">
    <h2 class="heading">Search and Find worker</h2>
    <div class="workerCards-section">
      <WorkAdCard
        v-for="(worker, index) in workers"
        :key="index"
        :name="worker.name"
        :place="worker.place"
        :state="worker.state"
        :description="worker.description"
        :hourlyRate="worker.hourlyRate"
      />
    </div>
  </div>
</template>

<script>
import WorkAdCard from "../components/WorkAdCard.vue";

export default {
  name: "Search",

  components: {
    WorkAdCard,
  },
  data() {
    return {
      workers: [],
    };
  },
  created() {
    fetch("https://panniapp.herokuapp.com/workers", {
      method: "GET",
      headers: {
        Accept: "application/json",
        "Content-Type": "application/json",
      },
    })
      .then((response) => response.json())
      .then((responseData) => {
        return (this.workers = responseData);
      })
      .catch((error) => console.warn(error));
  },
  methods: {},
};
</script>

<style scoped>
.container {
  margin: 2% 4%;
}
.heading {
  text-align: center;
  font-size: 20px;
}

.workerCards-section {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}

@media only screen and (max-width: 1000px) {
  /*Small smartphones [325px -> 425px]*/
}
@media only screen and (max-width: 550px) {
  /*Small smartphones [325px -> 425px]*/
}
</style>