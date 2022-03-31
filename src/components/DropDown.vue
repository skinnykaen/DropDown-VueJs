<template>
  <div class="dropDown">
    <span class="title">SEARCHABLE DROPDOWN</span>
    <SelectComponent></SelectComponent>
  </div>
</template>

<script>
import SelectComponent from "@/components/SelectComponent";
export default {
  components: {
    SelectComponent,
  },
};
</script>

<style>
.dropDown {
  padding-top: 3vh;
  weight: 100%;
  height: 100%;
}
</style>
