<template>
  <div class="employee">
    <h3>{{ employee.name }}</h3>
    <!-- Collapse section will show on clicking lightsaber -->
    <b-collapse :id="componentId" v-model="visible">
      <!-- Withou b-card element collapse dont work -->
      <b-card class="container">
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
      </b-card>
    </b-collapse>
    <!-- Clicking on lightsaber will show the details -->
    <img
      :class="visible ? null : 'collapsed'"
      :aria-controls="componentId"
      :aria-expanded="visible ? 'true' : 'false'"
      @click="visible = !visible"
      src="../assets/redLeftLightsaber.png"
      alt="red lightsaber"
      class="center"
    >
  </div>
</template>

<script>
export default {
  name: "Employee",
  props: { index: Number },

  data() {
    return {
      componentId: `collapse-${this.index}`,
      visible: false,
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
    const API = "https://swapi.dev/api/people/";

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


<style scoped>
/* General settings */
.employee {
  font-size: 0.8em;
}

.employee h3 {
  font-weight: normal;
  text-align: center;
  font-size: 1em;
}

/*  employee details available on click  */
.container {
  display: flex;
  background-color: rgb(43, 57, 66);
}
.leftCol {
  display: flex;
  flex-direction: column;
  align-items: center;
  line-height: 1em;
  float: left;
  width: 10em;
}

.leftCol p {
  /* Changing the space beetween the lines to match prototype */
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
  float: left;
  position: relative;
  left: 3em;
}

.middleCol p {
  /* Changing the space beetween the lines to match prototype*/
  margin: 1px;
  padding: 1px;
}

.rightCol {
  display: none;
  flex-direction: row;
  background-color: rgb(30, 40, 50);
  width: 5em;
  height: 5em;
  position: relative;
  left: 3em;
}

/* Center red lightsaber */
.center {
  display: block;
  margin-left: auto;
  margin-right: auto;
  position: relative;
  right: 1.25em;
  width: 100%;
}

/* Media breakpoints */

@media (min-width: 600px) {
  .middleCol {
    left: 1em;
  }

  .middleCol {
    left: 3em;
  }
  .rightCol {
    display: flex;
    left: 7em;
  }
}

@media (min-width: 800px) {
  .employee {
    font-size: 1.2em;
  }
  .middleCol {
    left: 2em;
  }
  .rightCol {
    position: relative;
    left: 7em;
  }
}

@media (min-width: 1000px) {
  .employee {
    font-size: 1.4em;
  }
  .middleCol {
    left: 4em;
  }
  .rightCol {
    position: relative;
    left: 10em;
  }
}

@media (min-width: 1200px) {
  .employee {
    font-size: 1.6em;
  }
  .middleCol {
    left: 6em;
  }
  .rightCol {
    position: relative;
    left: 14em;
  }
}
</style>