<template>
  <div class="switchTheme">
    <span>THEME</span>
    <div class="themes">
      <span class="dark" @click="toggleTheme">DARK</span>
      <span class="light" @click="toggleTheme">LIGHT</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      isDark: true,
    };
  },
  methods: {
    toggleTheme() {
      console.log("Хочу сменить тему");
      console.log(this.isDark)
      this.isDark = !this.isDark;
    },
  },
};
</script>

<style>
span {
  font-family: "Roboto";
  font-style: normal;
  font-weight: 400;
  font-size: 2vh;
  line-height: 15px;
}

.switchTheme {
  width: 40%;
  height: 100%;

  display: flex;
  justify-content: flex-start;
}
.themes {
  width: 100%;
  height: 100%;
  padding-left: 15%;
}
.themes :last-child {
  padding-left: 5%;
}
</style>
