<template>
  <div id="app">
    <div class="wrapper">
      <Starwars/>
      <ul class="employees">
        <li v-for="index in 7" :key="index">
          <Employee :index="index"/>
        </li>
      </ul>
    </div>
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
  overflow-y: hidden;
}
body {
  background-color: rgb(29, 42, 50);
  min-width: 420px;
}
.wrapper {
  border-radius: 2em;
  color: rgb(100, 110, 120);
  background-color: rgb(43, 57, 66);
}

ul {
  list-style-type: none;
}
</style>
