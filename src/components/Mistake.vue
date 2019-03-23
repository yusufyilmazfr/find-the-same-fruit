<template>
  <div class="mistake-content">
    <div>
      <img src="../images/sad.png" alt width="128">
      <h1 class="mistake-text">Ops!, Wrong Answer</h1>
      <button class="mistake-button" @click="changeComponent">New Game</button>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    changeComponent() {
      this.$emit("changeComponent", "AppGameCards");
    }
  }
};
</script>

<style scoped>
.mistake-content {
  font-family: "Times New Roman", Times, serif;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgb(233, 112, 112);
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.mistake-text {
  font-size: 45px;
  color: #fff;
}
.mistake-button {
  padding: 15px 25px;
  border-color: transparent;
  cursor: pointer;
  font-size: 15px;
  border-radius: 5px;
  background: #fff;
  color: rgb(233, 112, 112);
  font-weight: 700;
  letter-spacing: 2px;
  transition: background 0.5s;
  outline: none;
}
.mistake-button:hover {
  color: #fff;
  border: solid;
  border-color: #fff;
  background: transparent;
}
</style>