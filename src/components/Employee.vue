<template>
  <div class="hello">
    <h3>{{ employee.name }}</h3>
    <img src alt="red lightsaber">
  </div>
</template>

<script>
const API = "https://swapi.dev/api/people/";
export default {
  name: "Employee",
  props: { index: Number },
  data() {
    return {
      employee: {
        name: "???",
        additionalData: "someData"
      }
    };
  },
  created() {
    fetch(`${API}${this.index}/`)
      .then(response => response.json())
      .then(data => {
        this.employee.name = data["name"];
      });
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>