<template>
  <div id="app">
    <Starwars/>
    <ul class="employees">
      <li v-for="index in 7" :key="index">
        <Employee :index="index"/>
      </li>
    </ul>
  </div>
</template>

<script>
import Starwars from "./components/StarWars";
import Employee from "./components/Employee";

export default {
  name: "App",
  components: {
    Starwars,
    Employee
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

* {
  font-family: Roboto;
}
</style>
