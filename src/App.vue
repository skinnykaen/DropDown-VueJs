<template>
  <div class="app">
    <SwitchTheme></SwitchTheme>
    <DropDown></DropDown>
  </div>
</template>

<script>
import SwitchTheme from "@/components/SwitchTheme";
import DropDown from "@/components/DropDown";
export default {
  components: {
    SwitchTheme,
    DropDown
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.app {
  padding: 20px;
}
</style>