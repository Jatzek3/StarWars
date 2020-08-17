<template>
  <div class="employee">
    <h3>{{ employee.name }}</h3>
    <div class="additionalInfo">
      <div class="leftCol">
        <p>Height: {{ employee.height }} cm</p>
        <p>Mass: {{ employee.mass }} kg</p>
        <p>Birth Year: {{ employee.birth_year}}</p>
        <p>Gender: {{employee.gender}}</p>
      </div>
      <div class="middleCol">
        <p>Hair : {{employee.hair}}</p>
        <p>Skin: {{ employee.skin}}</p>
        <p>Eyes: {{employee.eyes}}</p>
      </div>
      <div class="rightCol"></div>
    </div>
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
        name: "",
        height: "",
        mass: "",
        birth_year: "",
        gender: "",
        hair: "",
        skin: "",
        eyes: ""
      }
    };
  },
  created() {
    fetch(`${API}${this.index}/`)
      .then(response => response.json())
      .then(data => {
        this.employee.name = data["name"];
        this.employee.height = data["height"];
        this.employee.mass = data["mass"];
        this.employee.birth_year = data["birth_year"];
        this.employee.gender = data["gender"];
        this.employee.hair = data["hair_color"];
        this.employee.skin = data["skin_color"];
        this.employee.eyes = data["eye_color"];
      });
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.employee {
  font-size: 0.8em;
}
.leftCol {
  display: flex;
  flex-direction: column;
  align-items: center;
  line-height: 0px;
}
.middleCol {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  line-height: 0px;
}
.rightCol {
  display: flex;
}
.additionalInfo {
  display: flex;
  justify-content: space-around;
}
</style>