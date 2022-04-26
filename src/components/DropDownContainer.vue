<template>
  <div v-if="isOpen" class="DropDownContainer">
    <SearchInput> </SearchInput>
    <DropDownList :items="items"> </DropDownList>
  </div>
</template>

<script>
import SearchInput from "@/components/SearchInput";
import DropDownList from "@/components/DropDownList";
export default {
  props: ["isOpen"],
   data() {
    return {
      items: [
        {
          key: "1",
          value: "Сегодня"
        },
        {
          key: "2",
          value: "Вчера"
        }
      ],
    };
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
  border: solid 1px #86d4e8;
  width: 20vw;
  min-height: 25vh;
}
</style>
