<template>
  <div class="app" :class="mode">
    <SwitchTheme @toggleTheme="toggleTheme"></SwitchTheme>
    <DropDown :mode="mode"></DropDown>
  </div>
</template>

<script>
import SwitchTheme from "@/components/SwitchTheme";
import DropDown from "@/components/DropDown";
export default {
  data() {
    return {
      mode: "light",
    };
  },
  components: {
    SwitchTheme,
    DropDown,
  },
  methods: {
    toggleTheme(mode) {
      this.mode = mode;
    },
  },
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
  box-sizing: border-box;
  width: 80%;
  height: 100%;
  padding: 2rem;
  width: 100vw;
  min-height: 100vh;
  transition: background 0.3s ease-in-out;
}

.app.light {
  background: #ffffff;
  color: #15202b;
}

.app.dark {
  background: #181F29;
  color: #e8e8e8;
}
</style>
