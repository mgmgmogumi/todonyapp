<template>
  <div class="container">
    <Header></Header>
    <Body></Body>
  </div>
</template>

<script>
import Header from "./components/Header.vue";
import Body from "./components/Body.vue";

export default {
  components: {
    Header,
    Body
  },
};
</script>

<style>
.container {
  width: 300px;
  margin: auto;
}
</style>