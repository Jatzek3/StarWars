<template>
  <div class="employee">
    <h3>{{ employee.name }}</h3>
    <div class="additionalInfo" v-bind:class="{ active: isActive }">
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
    <img
      @click="isActive?isActive=false:isActive=true"
      src="../assets/redLeftLightsaber.png"
      alt="red lightsaber"
      class="center"
    >
  </div>
</template>

<script>
const API = "https://swapi.dev/api/people/";
export default {
  name: "Employee",
  props: { index: Number },
  data() {
    return {
      isActive: false,
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
  methods: {
    applyActive() {}
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
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  position: relative;
  right: 1.25em;
  width: 100%;
}
.employee {
  font-size: 0.8em;
}
.employee h3 {
  font-weight: normal;
  text-align: center;
  font-size: 1em;
}
.leftCol {
  display: flex;
  flex-direction: column;
  align-items: center;
  line-height: 1em;

  width: 10em;
}
.leftCol p {
  margin: 1px;
  padding: 1px;
}
.middleCol {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  line-height: 1em;
  width: 10em;
}
.middleCol p {
  margin: 1px;
  padding: 1px;
}
.rightCol {
  display: flex;
  width: 10em;
}
.additionalInfo {
  display: none;
  justify-content: space-around;
}
.active {
  display: flex;
  justify-content: space-around;
}
</style>