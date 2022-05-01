<template>
  <li class="ListItem" @click="select">
    <span>{{ value }}</span>
  </li>
</template>

<script>
export default {
    props: ["value"],
    data() {
      return {
        selectValue: ''
      }
    },
    methods: {
      select(){
        this.selectValue = this.value;
        this.$emit('select', this.selectValue);
      }
    }
}
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
  background-color: #12171F;
  color: #86D4E8;
}
</style>
