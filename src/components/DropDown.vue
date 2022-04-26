<template>
  <div class="dropDown">
    <span class="title">SEARCHABLE DROPDOWN</span>
    <SelectComponent @dropDown="isOpenToggling"></SelectComponent>
    <DropDownContainer :isOpen="isOpen"></DropDownContainer>
  </div>
</template>

<script>
import SelectComponent from "@/components/SelectComponent";
import DropDownContainer from "@/components/DropDownContainer";
export default {
  components: {
    SelectComponent,
    DropDownContainer
  },
  data () {
    return {
      isOpen: false
    }
  },
  methods: {
    isOpenToggling(open){
     this.isOpen = open;
    }
  }
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
