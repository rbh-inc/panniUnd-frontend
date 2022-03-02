<template>
  <div class="container">
    <div class="search-filters">
      <h3 class="search-heading">Search and Filter</h3>

      <input type="text" placeholder="Location" />
      <input id="hourlyRate" type="number" max="1000" placeholder="Rate ₹" />

      <label for="dog-names">Sector: </label>
      <select class="select-dropdown" name="dog-names" id="dog-names">
        <option value="rigatoni">Any</option>
        <option value="dave">Dave</option>
        <option value="pumpernickel">Pumpernickel</option>
        <option value="reeses">Reeses</option>
      </select>

      <label for="dog-names">Sub-Sector: </label>
      <select class="select-dropdown" name="dog-names" id="dog-names">
        <option value="rigatoni">Any</option>
        <option value="dave">Dave</option>
        <option value="pumpernickel">Pumpernickel</option>
        <option value="reeses">Reeses</option>
      </select>

      <label for="dog-names">Sex: </label>
      <select class="select-dropdown" name="dog-names" id="dog-names">
        <option value="rigatoni">Any</option>
        <option value="dave">Male</option>
        <option value="pumpernickel">Female</option>
      </select>
      <button class="submit-btn">Search</button>
    </div>
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

.workerCards-section {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.search-filters {
  box-shadow: 0px 4px 6px 2px rgba(0, 0, 0, 0.1);
  padding: 5px;
  margin: 5px 10px;
  border-radius: 10px;
}
.select-dropdown {
  border: 1px solid #ccc;
  border-radius: 4px;
  margin: 4px;
  padding: 5px;
  background-color: #fff;
  font-size: 15px;
}

label {
  margin-left: 10px;
}

input {
  width: 175px;
  padding: 5px 5px;
  margin-left: 10px;
  display: inline-block;
  border: 1px solid #ccc;
  border-radius: 4px;
  box-sizing: border-box;
  font-size: 15px;
}

.search-heading {
  margin-left: 10px;
}
#hourlyRate {
  width: 75px;
}

.submit-btn {
  border: none;
  margin: 5px 10px;
  padding: 5px 10px;
  font-weight: bold;
  font-size: 18px;
  border-radius: 10px;
  background-color: #42b983;
  color: white;
}
/* Firefox */
input[type="number"] {
  -moz-appearance: textfield;
}
select {
  -moz-appearance: none; /* Firefox */
  -webkit-appearance: none; /* Safari and Chrome */
  appearance: none;
  background-image: url("data:image/svg+xml;utf8,<svg fill='black' height='24' viewBox='0 0 24 24' width='24' xmlns='http://www.w3.org/2000/svg'><path d='M7 10l5 5 5-5z'/><path d='M0 0h24v24H0z' fill='none'/></svg>");
  background-repeat: no-repeat;
  background-position-x: 100%;
  background-position-y: 3px;
}

@media only screen and (max-width: 1000px) {
  /*Small smartphones [325px -> 425px]*/
}
@media only screen and (max-width: 550px) {
  /*Small smartphones [325px -> 425px]*/
}
</style>