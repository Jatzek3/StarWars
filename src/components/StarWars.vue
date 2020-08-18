<template>
  <div class="starwars">
    <h1>Employees list</h1>
    <img src="../assets/blueLightsaber.png" alt="blue lightsaber" class="center">
  </div>
</template>

<script>
export default {
  name: "Starwars"
};
</script>

<style scoped>
.starwars h1 {
  color: rgb(160, 170, 180);
  font-weight: normal;
  font-size: 1.2em;
  padding-left: 3em;
  padding-top: 1em;
}
/* Center the lightsaber */
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 95%;
}

/* Media Breakpoints */
@media (min-width: 600px) {
  .starwars h1 {
    font-size: 1.5em;
  }
}
@media (min-width: 800px) {
  .starwars h1 {
    font-size: 2em;
  }
}
@media (min-width: 1000px) {
  starwars h1 {
    font-size: 2.5em;
  }
}
@media (min-width: 1200px) {
  starwars h1 {
    font-size: 3em;
  }
}
</style>
