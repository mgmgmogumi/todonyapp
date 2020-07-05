<template>
  <div>
    <h1>
      {{ title }}
      <img class="icon" src="../assets/footprint.png" />
    </h1>
    <img src="../assets/sleepy_cat.jpg" />
    <hr />
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: "TODO ニャプリ",
    };
  }
};
</script>

<style scoped>
#app h1 {
  font-size: 16;
}

.icon {
  width: 32px;
  height: 32px;
}

img {
  width: 100%;
  max-width: 100%;
  height: auto;
}

hr {
  border: 1px solid #ddd;
  margin-top: 20px;
}
</style>