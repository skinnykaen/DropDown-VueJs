<template>
  <li class="ListItem">
    {{ value }}
  </li>
</template>

<script>
export default {
  props: ["value"],
};
</script>

<style>
.ListItem {
  padding: 0.5em;
  width: 100%;
  min-height: 2.5rem;
  list-style-type: none;
}
.ListItem:hover {
  background-color: #86D4E8;
}
</style>
