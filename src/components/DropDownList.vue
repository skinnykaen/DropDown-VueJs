<template>
  <div>
    <div class="DropDownList" v-for="item in items" :key="item.key">
      <li>{{ item.value }}</li>
    </div>
  </div>
</template>

<script>
// import ListItem from "@/components/ListItem";
export default {
  props: ["items"],
//   components: {
//     ListItem,
//   },
};
</script>

<style>
.DropDownList {
  padding: 0;
}
</style>
