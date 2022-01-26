<template>
  <div class="container">
    <div class="sector-title">
      <h1>Sectors</h1>
    </div>

    <div class="sector-list">
      <div class="sector-list-card">
        <img src="https://img.icons8.com/fluency/96/000000/home.png" />
        <p>House Worker</p>
      </div>
      <div class="sector-list-card">
        <img src="https://img.icons8.com/clouds/50/000000/dinner-hotel.png" />
        <p>House Worker</p>
      </div>
      <div class="sector-list-card">
        <img
          src="https://img.icons8.com/external-flatart-icons-flat-flatarticons/50/000000/external-agriculture-agriculture-flatart-icons-flat-flatarticons.png"
        />
        <p>House Worker</p>
      </div>
      <div class="sector-list-card">
        <img
          src="https://img.icons8.com/external-justicon-lineal-color-justicon/50/000000/external-mechanic-avatar-and-occupation-justicon-lineal-color-justicon.png"
        />
        <p>House Worker</p>
      </div>
      <div class="sector-list-card">
        <img
          src="https://img.icons8.com/external-justicon-lineal-color-justicon/50/000000/external-hospital-hospital-justicon-lineal-color-justicon.png"
        />
        <p>House Worker</p>
      </div>
      <div class="sector-list-card">
        <img
          src="https://img.icons8.com/external-becris-flat-becris/50/000000/external-education-literary-genres-becris-flat-becris.png"
        />
        <p>House Worker</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "SectorCategories",
};
</script>

<style scoped>
.container {
  background-color: #262c31;

  width: 100%;
  margin: 20px 0 15px 0;
  display: flex;
  flex-direction: column;
  color: white;
}

.sector-title {
  margin-top: 10px;
  text-align: center;
}

.sector-list {
  display: flex;
  margin: 0px 30px 20px 30px;
}

.sector-list-card {
  margin: 2px 5px;
  display: flex;
  flex-direction: column;
  align-items: center;
  background-color: white;
  border-radius: 5px;
  box-shadow: #fbf1ed;
  height: 130px;
  width: 130px;
}
.sector-list-card img {
  width: 60px;
  padding-top: 15px;
}
.sector-list-card p {
  color: #262c31;
  margin: 10px;
}
</style>


