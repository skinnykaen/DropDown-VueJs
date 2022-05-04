<template>
  <div class="selectComponent" @click="dropDown">
    <span v-if="typeof this.choice === 'string'">{{ choice }}</span>
    <span v-else>{{ choice[0] ? choice[0] : "Выберите" }}</span>
    <div
      class="arrowUp"
      v-if="(choice !== '' || choice.length !== 0) && isOpen"
      @click.stop="clearSelect"
    >
      X
    </div>
    <div class="arrowDown" v-else>V</div>
  </div>
</template>

<script>
export default {
  props: {
    choice: {
      type: [String, Array],
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
    clearSelect() {
      this.$emit("clearSelect");
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
