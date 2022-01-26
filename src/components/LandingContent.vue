<template>
  <div id="container">
    <div class="main-section">
      <div class="landing-title">
        <h2>
          Find a <br />
          <span>freelancer</span>
        </h2>
      </div>
      <div class="landing-description">
        <p>
          Lorem ipsum dolor sit, amet consectetur adipisicing elit. Natus,
          expedita necessitatibus. Accusamus vitae quis ex cum obcaecati sed
          soluta labore autem.
        </p>
      </div>
      <div class="landing-btns">
        <button><router-link to="/about">I am a worker</router-link></button>
        <button><router-link to="/about">Find a worker</router-link></button>
      </div>
    </div>
    <div class="main-illustration">
      <img src="../assets/underConstruction.svg" alt="" />
    </div>
  </div>
</template>

<script>
export default {
  name: "LandingContent",
};
</script>

<style scoped>
#container {
  margin: 20px 30px 0 30px;
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  height: 40%;
}
.main-section {
  width: 50%;
  margin-top: 40px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
.landing-title h2 {
  font-size: 45px;
  margin-left: 10px;
}
.landing-title span {
  font-size: 50px;
  margin-left: 25px;
}

.main-illustration {
  width: 45%;
}

.landing-btns button {
  border: none;
  margin: 20px 20px 0px 20px;
  padding: 10px 20px 10px 20px;
  font-weight: bold;
  background-color: #d97356;
  border: solid 1px #ae5c45;
  color: white;
}

.main-illustration img {
  width: 550px;
}
</style>
