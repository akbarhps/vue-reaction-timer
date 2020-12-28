<template>
  <h1>{{ score }} ms</h1>
  <h2>{{ message }}</h2>
</template>

<script>
export default {
  props: ["score"],
  data() {
    return {
      message: null,
    };
  },
  mounted() {
    if (this.score < 300) {
      this.message = "da ril ninjaa";
    } else if (this.score < 500) {
      this.message = "not bad la mait";
    } else {
      this.message = "nuuuuuub";
    }
  },
};
</script>