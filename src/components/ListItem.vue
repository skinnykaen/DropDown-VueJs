<template>
  <li class="ListItem">
    {{value}}
  </li>
</template>

<script>
export default {
    props: ["value"],
}
</script>

<style>
.ListItem {
  padding: 0.5em;

}
.ListItem :hover {
  padding: 0.5em;
  background: red;
}
</style>
