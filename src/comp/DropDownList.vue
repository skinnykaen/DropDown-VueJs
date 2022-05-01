<template>
  <div class="DropDownList">
    <!-- <div v-for="item in items" :key="item.id">
      <ListItem :value="item.name" :class="mode" @select="selectOnChange"> </ListItem>
    </div> -->
  </div>
</template>

<script>
// import ListItem from "@/components/ListItem";
export default {
  props: ["items", "mode"],
  components: {
    // ListItem,
  },

  data () {
    return {
      choice: {},
    }
  },
  methods: {
    selectOnChange(select) {
      this.items.forEach((item) => {
        if (item.name === select) this.choice = item;
      });
      this.$emit("select", this.choice);
    },
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
