<template>
  <div id="nav">
    <div class="nav-title">
      <h1>xyz<span>.</span>app</h1>
    </div>
    <div class="nav-links">
      <ul>
        <li><router-link to="/">Home</router-link> |</li>
        <li><router-link to="/register">Worker Registration</router-link> |</li>
        <li><router-link to="/search">Find Worker</router-link></li>
      </ul>
    </div>
  </div>
</template>

<style scoped>
#nav {
  padding: 10px 20px 10px 20px;
  display: flex;
  justify-content: space-between;
  flex-direction: row;
}

.nav-title {
  color: #262c31;
  font-size: 20px;
}
span {
  color: #d87355;
  font-weight: bolder;
  font-size: 30px;
}
.nav-links {
  margin-top: 15px;
  font-weight: bold;
  color: #2c3e50;
  margin-right: 10px;
}
.nav-links li {
  display: inline;
  margin-left: 10px;
}

a {
  text-decoration: none;
}

a.router-link-exact-active {
  color: #42b983;
}
</style>
