<template>
  <div class="container">
    <div class="search-filters">
      <h3 class="search-heading">Search and Filter</h3>

      <input v-model="location" type="text" placeholder="Location" />
      <input id="hourlyRate" type="number" v-model="rate" placeholder="₹ Max" />

      <label>Sector: </label>
      <select v-model="sector" class="select-dropdown">
        <option
          v-for="(sector, indxSector) in chooseSectors"
          :key="indxSector"
          :value="sector"
        >
          {{ sector }}
        </option>
      </select>

      <label>SubSector: </label>
      <select v-model="subSector" class="select-dropdown">
        <option
          v-for="(subSector, indxSubSector) in chooseSubSectors"
          :key="indxSubSector"
          :value="subSector"
        >
          {{ subSector }}
        </option>
      </select>

      <label>Sex: </label>
      <select v-model="sex" class="select-dropdown">
        <option value="male">Male</option>
        <option value="female">Female</option>
      </select>
      <button @click="submitBtn()" class="submit-btn">Search</button>
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
      chooseSectors: [
        "Textile and apparels",
        "Food and dining",
        "Healthcare and wellness ",
        "Education",
        "Computer and mobile",
        "Home care service",
        "Automobile",
      ],
      chooseSubSectors: [
        "Cutting master",
        "Button operator",
        "Trimming staff",
        "Finishing Helper",
        "Machine Mechanic",
        "Qc checker",
        "Button hole operator",
        "Iron machine operators",
        "Tailor",
        "Helper",
        "Chef",
        "Waiter",
        "Receptionist",
        "Sous chef",
        "Commi chef",
        "Indian chef",
        "Chinese chef",
        "Arabic chef",
        "Continental chef",
        "Nurse",
        "Physiotherapist",
        "Nutritionist",
        "Psychiatrist",
        "Optometrist",
        "Pharmacist",
        "Doctor",
        "Lab technician",
        "OT assistant",
        "Ambulance driver",
        "Home nurse",
        "Subject experts",
        "Lab assistant",
        "Trainer",
        "Mentor",
        "Professor",
        "Computer technician",
        "Mobile technician",
        "Software developer",
        "Graphic designer",
        "Electrician",
        "Plumber",
        "Carpenter",
        "Mason",
        "Gardener",
        "Home maid",
        "Painter",
        "Flooring",
      ],
      location: "",
      rate: "",
      sector: "",
      subSector: "",
      sex: "",
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
  methods: {
    submitBtn() {
      const queryString = new URLSearchParams({
        location: this.location.trim(),
        rate: this.rate,
        sector: this.sector.trim(),
        subSector: this.subSector.trim(),
        sex: this.sex.trim(),
      });

      let url =
        "https://panniapp.herokuapp.com/query?" + queryString.toString();
      // console.log(url);
      this.apiCaller(url);
    },
    apiCaller(url) {
      fetch(url, {
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
  },
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
  min-width: 130px;
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

/* down arrow in selection sector and subsector */

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