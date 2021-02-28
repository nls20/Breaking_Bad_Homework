<template>
  <h2>{{ title }}</h2>
</template>

<script>
export default {
  name: "character-header",
  props: ["title"]
};
</script>

<style scoped>
h2 {
  font-size: 40px;
  color: white;
  padding: 5px;
  text-align: center;
  border-style: solid;
}
</style>