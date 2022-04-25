<template>
  <div class="app" :class="mode">
    <SwitchTheme @toggleTheme="toggleTheme"></SwitchTheme>
    <DropDown ></DropDown>
  </div>
</template>

<script>
import SwitchTheme from "@/components/SwitchTheme";
import DropDown from "@/components/DropDown";
export default {
  data () {
    return {
      mode: 'light'
    }
  },
  components: {
    SwitchTheme,
    DropDown,
  },
  methods: {
    toggleTheme(mode){
     this.mode = mode;
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Roboto", sans-serif;
}
.app {
  padding: 2rem;
  width: 100vw;
  min-height: 100vh;
  background: #FFFFFF;
  color: #15202b;
  transition: background 0.3s ease-in-out;
}
.dark {
  background: #181F29;
  color: #E8E8E8;
}
</style>
