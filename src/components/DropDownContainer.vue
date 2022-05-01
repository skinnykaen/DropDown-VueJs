<template>
  <div v-if="isOpen" class="DropDownContainer">
    <SearchInput v-if="search" @input="searchChange" :class="mode">
    </SearchInput>
    <div v-else></div>
    <DropDownList :items="searchItems" :mode="mode" @select="selectChange"> </DropDownList>
  </div>
</template>

<script>
import SearchInput from "@/components/SearchInput";
import DropDownList from "@/components/DropDownList";
export default {
  props: {
    isOpen: { type: Boolean, default: false },
    mode: { type: String, default: "ligth" },
    search: { type: Boolean, default: false },
    items: { type: [Array, Function], default: () => [] },
  },
  data() {
    return {
      searchItems: [...this.items],
      choice: {}
    };
  },
  methods: {
    searchChange(input) {
      if (input) {
        this.searchItems = this.items.filter(item => (item.name.includes(input)));
      } else {
        this.searchItems = this.items;
      }
    },
    selectChange(select){
      this.choice = select;
      this.$emit("select", this.choice);
    }
  },
  components: {
    SearchInput,
    DropDownList,
  },
};
</script>

<style>
.DropDownContainer {
  display: flex;
  justify-content: flex-start;
  align-items: center;
  flex-direction: column;
  box-sizing: border-box;
  margin-top: 10px;
  border-radius: 5px;
  border: solid 1px grey;
  width: 20vw;
  min-height: 20vh;
}
</style>
