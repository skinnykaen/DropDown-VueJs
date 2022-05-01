<template>
  <div class="dropDown">
    <span class="title">SEARCHABLE DROPDOWN</span>
    <SelectComponent @dropDown="isOpenToggling" :value="choice.name"></SelectComponent>
    <DropDownContainer
      :isOpen="isOpen"
      :mode="mode"
      :search="search"
      :items="items"
      @select="selectChange"
    ></DropDownContainer>
  </div>
</template>

<script>
import SelectComponent from "@/components/SelectComponent";
import DropDownContainer from "@/components/DropDownContainer";
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
    SelectComponent,
    DropDownContainer,
  },
  data() {
    return {
      isOpen: false,
      choice: {},
    };
  },
  methods: {
    isOpenToggling(open) {
      this.isOpen = open;
    },
    selectChange(select){
      this.choice = select;
    }
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
</style>
