<template>
  <div class="DropDownList">
    <div v-for="item in items" :key="item.id">
      <ListItem :value="item.name" :class="mode"> </ListItem>
    </div>
  </div>
</template>

<script>
import ListItem from "@/components/ListItem";
export default {
  props: ["items", "mode"],
  components: {
    ListItem,
  },
};
</script>

<style>
.DropDownList {
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
