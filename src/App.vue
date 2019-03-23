<template>
  <transition mode="out-in" name="slide">
    <component :is="componentName" @changeComponent="componentName = $event"></component>
  </transition>

  <!-- <app-game-cards></app-game-cards> -->
  <!-- <app-mistake></app-mistake> -->
</template>


<script>
import CustomCard from "./components/CustomCard";
import GameCards from "./components/GameCards";
import Clap from "./components/Clap";
import Mistake from "./components/Mistake";

export default {
  data() {
    return {
      componentName: "AppGameCards"
    };
  },
  components: {
    AppGameCards: GameCards,
    AppClap: Clap,
    AppMistake: Mistake
  }
};
</script>

<style>
body {
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
  /* background-color : rgb(95, 99, 100); */
}
.Container {
  margin-top: 30px;
  margin-bottom: 30px;
}
.header-text {
  text-align: center;
}
.header-text > h1,
p {
  margin: 0;
}
.slide-enter-active{
  animation: slide-start .1s;
}
.slide-leave-active{
  animation: slide-end .4s;
}
@keyframes slide-end{
  from{
    transform: translateX(0);
  }
  to{
    transform: translateX(9999px);
  }
}
@keyframes slide-start {
  from{
    transform: translateX(-9999px);
  }
  to{
    transform: translateX(0px);
  }
}
</style>