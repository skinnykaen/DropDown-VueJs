<template>
  <div class="SearchInput">
    <input @input="updateInput" type="text" placeholder="Поиск" />
  </div>
</template>

<script>
export default {
  methods: {
    updateInput(event) {
      this.$emit("input", event.target.value);
    },
  },
};
</script>

<style>
.SearchInput {
  margin-top: 0.5em;
  border-radius: 5px;
  border: solid 2px grey;
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
  font-family: "Roboto";
  font-style: normal;
  font-weight: 400;
  font-size: 2vh;
  line-height: 15px;
}
.SearchInput.dark input::placeholder {
  color: #828282;
}
.SearchInput.dark input {
  background-color: #293341;
  color: white;
}
.SearchInput.light input {
  background-color: none;
  color: black;
}
</style>
