<template>
  <div class="switchTheme">
    <span>THEME</span>
    <div class="themes">
      <span class="darkTheme" @click="toggleTheme">DARK</span>
      <span class="lightTheme" @click="toggleTheme">LIGHT</span>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mode: "light",
    };
  },
  methods: {
    toggleTheme(e) { 
      if(e.target.className === "darkTheme"){
        this.mode = "dark"
      }else{
        this.mode = "light"
      }
      this.$emit('toggleTheme', this.mode)
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
