<template>
  <div class="max-w-sm rounded overflow-hidden shadow-lg">
    <img class="w-full" :src="game.keyImages[1].url" alt="jpg" />
  </div>
</template>

<script>
export default {
  name: "CardPC",
  props: ["game"],
};
</script>