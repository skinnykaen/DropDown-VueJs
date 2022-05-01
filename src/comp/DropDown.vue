<template>
  <div class="dropDown">
    <span class="title">SEARCHABLE DROPDOWN</span>
    <SelectComponent @dropDown="isOpenToggling" @clearSelect="clearSelect" :value="choice" />
    <div v-if="isOpen" class="dropDown__content">
      <SearchInput v-if="search" @input="searchOnChange" :class="mode" />
      <div v-else></div>
      <div class="dropDown__list">
        <div v-for="item in searchItems" :key="item.id">
          <ListItem :value="item.name" :class="mode" @select="selectOnChange" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SearchInput from "@/comp/SearchInput";
import SelectComponent from "@/comp/SelectComponent";
import ListItem from "@/comp/ListItem";
export default {
  props: {
    mode: { type: String, default: "light", required: true },
    value: { type: [Array, Object, String, Number], required: true },
    search: { type: Boolean, default: false },
    items: { type: [Array, Function], required: true },
    display: { type: Function },
    nullable: { type: Boolean },
  },
  components: {
    SearchInput,
    SelectComponent,
    ListItem,
  },
  data() {
    return {
      isOpen: false,
      choice: [{ name: "Выберите" }],
      searchItems: [...this.items].slice(0, 20),
    };
  },
  methods: {
    isOpenToggling(open) {
      this.isOpen = open;
      if (!this.isOpen) {
        this.searchItems = this.items.slice(0, 20);
      }
    },
    clearSelect() { 
      this.choice = [{name: "Выберите"}]
    },
    searchOnChange(input) {
      if (input) {
        this.searchItems = this.items.filter((item) => item.name.toLowerCase().includes(input.toLowerCase())).slice(0,20);
      } else {
        this.searchItems = this.items.slice(0, 20);
      }
    },
    selectOnChange(select) {
      this.choice = this.items.filter((item) => item.name === select);
    },
  },
};
</script>

<style>
.dropDown {
  box-sizing: border-box;
  padding-top: 3vh;
  width: 100%;
  height: 100px;
}
.dropDown__content {
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
.dropDown__list {
  width: 100%;
  max-height: 21vh;
  box-sizing: border-box;
  overflow: auto;
}
::-webkit-scrollbar {
  width: 10px;
}

::-webkit-scrollbar-thumb {
  background-color: grey;
}
</style>
