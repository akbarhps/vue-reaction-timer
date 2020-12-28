<template>
  <div class="backdrop" @click.self="closeResult">
    <div class="modal dark">
      <h1>your reaction time is: <br />{{ score }} ms</h1>
      <h2>{{ message }}</h2>
      <button @click="closeResult">Close</button>
    </div>
  </div>
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
  methods: {
    closeResult() {
      this.$emit("closeResult");
    },
  },
};
</script>

<style>
.backdrop {
  top: 0;
  position: fixed;
  background: black;
  width: 100%;
  display: flex;
  height: 100%;
  align-content: center;
}
.modal {
  width: 400px;
  height: 200px;
  padding: 50px;
  margin: auto;
  background: black;
  color: white;
  border-radius: 10px;
}
.modal .actions a {
  padding: 8px;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
  color: white;
  border: 1px solid #eee;
}
</style>