<template>
  <div class="dropDown">
    <span class="title">SEARCHABLE DROPDOWN</span>
    <SelectComponent
      @dropDown="isOpenToggling"
      @clearSelect="clearSelect"
      :valueN="choice"
    />
    <div v-if="isOpen" class="dropDown__content">
      <SearchInput
        v-model="searchInput"
        v-if="search"
        @input="searchOnChange"
        :class="mode"
      />
      <div v-else></div>
      <div class="dropDown__list">
        <div v-for="item in searchItems" :key="item.id">
          <ListItem
            :valueN="item.name"
            :class="mode"
            :multiple="multiple"
            @select="selectOnChange"
            @checked="checkedOnChange"
          />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SearchInput from "@/DropDown/SearchInput";
import SelectComponent from "@/DropDown/SelectComponent";
import ListItem from "@/DropDown/ListItem";
export default {
  props: {
    mode: { type: String, default: "light", required: true },
    value: { type: [Array, Object, String, Number], required: true },
    search: { type: Boolean, default: false },
    multiple: { type: Boolean, default: false },
    items: { type: [Array, Function], required: true },
    display: { type: Function },
    nullable: { type: Boolean },
    valueN: {type: String, Array}
  },
  components: {
    SearchInput,
    SelectComponent,
    ListItem,
  },
  data() {
    let typeOfChoice;
    if (typeof this.value === "string") {
      typeOfChoice = "";
    } else {
      typeOfChoice = [];
    }
    return {
      isOpen: false,
      choice: typeOfChoice,
      searchItems: [...this.items].slice(0, 20),
      searchInput: "",
    };
  },
  methods: {
    isOpenToggling(open) {
      this.isOpen = open;
    },
    clearSelect() {
      this.searchInput = "";
      if (typeof this.choice === "string") {
        this.choice = "";
      } else {
        this.choice = [];
      }
      this.searchItems = this.items.slice(0, 20);
    },
    searchOnChange(input) {
      if (input) {
        this.searchItems = this.items
          .filter((item) => item.name.toLowerCase().includes(input.toLowerCase()))
          .slice(0, 20);
      } else {
        this.searchItems = this.items.slice(0, 20);
      }
    },
    selectOnChange(select) {
      if (this.multiple) {
        let find = this.items.find((item) => item.name === select);
        this.choice.push(find);
      } else {
        this.choice = this.items.find((item) => item.name === select);
        this.searchItems = [];
        this.searchItems.push(this.choice);
      }
    },
    checkedOnChange(checked) {
      let find = this.items.find((item) => item.name === checked);
      console.log(find)
      let already = this.choice.find(item => item.name === find.name);
      if(!already){
        this.choice.push(find)
      }else{
        this.choice = this.choice.filter(item => item.name !== find.name)
      }
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
