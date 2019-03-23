<template>
    <div class="game-card" >
      <img :src="card.Image" alt="this is a fruit">
    </div>
</template>


<script>
export default {
    props : ["card"]
}
</script>

<style>
.shadow {
  box-shadow: 2px 0px 20px 12px #ddd !important;
}
</style>