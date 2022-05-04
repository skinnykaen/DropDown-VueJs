<template>
  <li v-if="!multiple" class="ListItem" @click="select">
    <span>{{ value }}</span>
  </li>
  <div class="ListItem" v-else>
    <input type="checkbox" @click="checked" />
    {{ value }}
  </div>
</template>

<script>
export default {
  props: ["value", "multiple"],
  data() {
    return {
      selectValue: "",
    };
  },
  methods: {
    select() {
      this.selectValue = this.value;
      this.$emit("select", this.selectValue);
    },
    checked() {
      this.selectValue = this.value;
      this.$emit("checked", this.selectValue);
    },
  },
};
</script>

<style>
.ListItem {
  padding: 0.5em;
  width: 100%;
  min-height: 2.5rem;
  list-style-type: none;
  cursor: pointer;
}
.ListItem.dark {
  color: white;
}
.ListItem.light {
  color: black;
}
.ListItem.light:hover {
  background-color: #86d4e8;
}
.ListItem.dark:hover {
  background-color: #12171f;
  color: #86d4e8;
}
</style>
