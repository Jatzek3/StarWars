<template>
  <div id="app">
    <div class="wrapper">
      <Starwars/>
      <ul class="employees">
        <draggable v-model="count" @start="drag=true" @end="drag=false">
          <transition-group>
            <li v-for="index in count" :key="index">
              <Employee :index="index"/>
            </li>
          </transition-group>
        </draggable>
      </ul>
    </div>
  </div>
</template>

<script>
import Starwars from "./components/StarWars";
import Employee from "./components/Employee";
import draggable from "vuedraggable";

export default {
  name: "App",
  components: {
    Starwars,
    Employee,
    draggable
  },
  data() {
    return {
      count: [1, 2, 3, 4, 5, 6, 7]
    };
  }
};
</script>
<style>
/* General Setup */
@import url("https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap");

* {
  font-family: Roboto;
  overflow: hidden;
}
body {
  background-color: rgb(29, 42, 50);
  min-width: 480px;
}
/* Application  */
.wrapper {
  margin: 1em;
  border-radius: 0.5em;
  color: rgb(100, 110, 120);
  background-color: rgb(43, 57, 66);
}
ul {
  list-style-type: none;
}
</style>
