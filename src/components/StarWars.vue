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
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 95%;
}
</style>
