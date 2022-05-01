<template>
  <div class="selectComponent">
    <span>{{value}}</span>
    <div class="arrowDown" v-if="!isOpen" @click="dropDown">V</div>
    <div class="arrowUp" v-else @click="dropDown">X</div>
  </div>
</template>

<script>
export default {
  props: {
    value: {
      type: String,
      default: "Выберите период"
    },
  },
  data() {
    return {
      isOpen: false,
    };
  },
  methods: {
    dropDown() {
      this.isOpen = !this.isOpen;
      this.$emit("dropDown", this.isOpen);
    },
  },
};
</script>

<style>
.selectComponent {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 20vw;
  height: 5vh;
  border-radius: 5px;
  border: solid 1px grey;
  margin-top: 1em;
}
.selectComponent span {
  color: grey;
  margin-left: 0.5em;
}
.selectComponent .arrowDown {
  position: absolute;
  left: 20vw;
  color: grey;
  margin-right: 0.5em;
  cursor: pointer;
}
.selectComponent .arrowUp {
  position: absolute;
  left: 20vw;
  color: grey;
  margin-right: 0.5em;
  cursor: pointer;
}
</style>
