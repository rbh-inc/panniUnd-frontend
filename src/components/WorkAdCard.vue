<template>
  <div ref="card" class="card">
    <div class="card-header">
      <div>
        <h4 class="card-title">{{ name ? name : "Some Title" }}</h4>
        <p class="card-location">
          <img
            class="location-icon"
            src="../assets/location-icon.png"
            alt=""
          />{{ place ? place : "Place" }} &bull; {{ state ? state : "State" }}
        </p>
      </div>
      <div>
        <p class="card-day">23</p>
        <span class="card-month">JAN</span>
      </div>
    </div>
    <div class="card-body">
      <p>
        {{
          description
            ? description
            : "Lorem ipsum dolor sit amet consectetur adipisicing elit."
        }}
      </p>
    </div>
    <div class="card-footer">
      <p>
        <spam>₹ </spam>{{ hourlyRate ? hourlyRate : 250 }} <span>hour</span>
      </p>
      <a class="hire-btn" href="">HIRE</a>
    </div>
  </div>
</template>

<script>
export default {
  name: "WordAdCard",
  props: ["name", "place", "description", "hourlyRate", "state"],
};
</script>


<style scoped>
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  border-radius: 5px;
  height: 185px;
  width: 360px;
  margin: 10px;
  font-family: "Work Sans", sans-serif;
  border-top: solid 4px gold;
}

.card-header {
  margin: 15px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}

.card-body {
  margin: 15px;
}
.card-footer {
  margin: 15px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
span {
  font-size: 14px;
  font-weight: bold;
}
.card-title {
  font-size: 20px;
}
.card-location {
  font-size: 14px;
  margin: 5px;
}

.hire-btn {
  color: #42b983;
  font-weight: bold;
}
.location-icon {
  width: 20px;
  margin: -3px;
  margin-right: 3px;
}

@media (max-width: 979px) {
  .card {
    width: 250px;
    height: 200px;
  }
}
@media (max-width: 600px) {
  .card {
    width: 350px;
    height: 200px;
  }
}
</style>
