<template>
  <div class="SearchInput">
    <input v-model.trim="search" @input="updateInput" type="text" placeholder="Поиск" />
  </div>
</template>

<script>
export default {
  data() {
    return {
      search: "",
    };
  },
  methods: {
    updateInput(event) {
      this.$emit("update:modelValue", event.target.value);
    },
  },
};
</script>

<style>
.SearchInput {
  margin-top: 0.5em;
  border-radius: 5px;
  border: solid 1px grey;
  width: 95%;
  height: 4vh;
  margin-bottom: 0.5em;
}
.SearchInput input {
  width: 100%;
  height: 100%;
  padding: 1rem;
  border: none;
  outline: none;
  background: none;
  color: white;
  font-family: "Roboto";
  font-style: normal;
  font-weight: 400;
  font-size: 2vh;
  line-height: 15px;
}
</style>
