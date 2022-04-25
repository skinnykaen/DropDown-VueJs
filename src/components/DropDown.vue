<template>
  <div class="dropDown">
    <span class="title">SEARCHABLE DROPDOWN</span>
    <SelectComponent @dropDown="isOpenToggling"></SelectComponent>
    <DropDownList :isOpen="isOpen"></DropDownList>
  </div>
</template>

<script>
import SelectComponent from "@/components/SelectComponent";
import DropDownList from "@/components/DropDownList";
export default {
  components: {
    SelectComponent,
    DropDownList
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
