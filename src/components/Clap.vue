<template>
  <div class="clap-content">
    <div>
      <img src="../images/happy.png" alt width="128">
      <h1 class="clap-text">Yess, continue <3 </h1>
      <button class="clap-button" @click="changeComponent">New Game</button>
    </div>
  </div>
</template>

<script>
export default {
    methods : {
        changeComponent(){
            this.$emit('changeComponent','AppGameCards')
        }
    }
}
</script>

<style>
.clap-content {
  font-family: "Times New Roman", Times, serif;
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgb(85, 252, 154);
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}
.clap-text {
  font-size: 45px;
  color: rgb(69, 78, 124);
}
.clap-button {
  padding: 15px 25px;
  border-color: transparent;
  cursor: pointer;
  font-size: 15px;
  border-radius: 5px;
  background: rgb(69, 78, 124);
  color: rgb(85, 252, 154);
  font-weight: 700;
  letter-spacing: 2px;
  transition: background 0.5s;
  outline: none;
}
.clap-button:hover {
  color: rgb(69, 78, 124);
  border: solid;
  border-color: rgb(69, 78, 124);
  background: transparent;
}
</style>
