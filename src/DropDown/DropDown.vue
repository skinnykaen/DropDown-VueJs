<template>
  <div
    class="dropDown"
    v-bind:value="value"
    v-on:input="$emit('input', $event.target.value)"
  >
    <span class="dropDown__title">SEARCHABLE DROPDOWN</span>
    <SelectComponent
      @dropDown="isOpenToggling"
      @clearSelect="clearSelect"
      :choice="choice"
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
          <!-- <ListItem
            :class="mode"
            :multiple="multiple"
            :value="item.name"
            @select="selectOnChange"
            @checked="checkedOnChange"
          /> -->
          <div v-if="!multiple" class="dropDown__listItem" :class="mode">
            <label>{{ item.name }}</label>
          </div>
          <div v-else class="dropDown__listItem" :class="mode">
            <input type="checkbox" :value="item.name" v-model="choice" />
            <label>{{ item.name }}</label>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import SearchInput from "@/DropDown/SearchInput";
import SelectComponent from "@/DropDown/SelectComponent";
// import ListItem from "@/DropDown/ListItem";
export default {
  props: {
    // Тема
    mode: { type: String, default: "light", required: true },
    // Тип входного значения
    value: { type: [Array, Object, String, Number], required: true },
    // Нужна ли строка поиска
    search: { type: Boolean, default: false },
    // Множественный выбор
    multiple: { type: Boolean, default: false },
    // Список вариант
    items: { type: [Array, Function], required: true },
    // Преобразование к строке
    display: { type: Function },
    // ???
    nullable: { type: Boolean },
  },
  components: {
    SearchInput,
    SelectComponent,
    // ListItem,
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
      checked: [],
    };
  },
  methods: {
    isOpenToggling(open) {
      this.isOpen = open;
    },
    ff(event){
      console.log(event)
    }
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
      console.log(find);
      let already = this.choice.find((item) => item.name === find.name);
      if (!already) {
        this.choice.push(find);
      } else {
        this.choice = this.choice.filter((item) => item.name !== find.name);
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

.dropDown__listItem {
  padding: 0.5em;
  width: 100%;
  min-height: 2.5rem;
  list-style-type: none;
  cursor: pointer;
}
.dropDown__listItem.dark {
  color: white;
}
.dropDown__listItem.light {
  color: black;
}
.dropDown__listItem.light:hover {
  background-color: #86d4e8;
}
.dropDown__listItem.dark:hover {
  background-color: #12171f;
  color: #86d4e8;
}

::-webkit-scrollbar {
  width: 10px;
}

::-webkit-scrollbar-thumb {
  background-color: grey;
}
</style>
