<script setup lang="ts">
type Props = {
  currentBeer?: number;
};

const { currentBeer = 0 } = defineProps<Props>();

const chooseBeerImage = (index: number) => {
  if (index === currentBeer + 1) {
    return "assets/beer_last.png";
  }

  if (index === currentBeer + 2) {
    return "assets/beer_prelast.png";
  }

  if (currentBeer >= index) {
    return "assets/beer.gif";
  }

  return "assets/beer.png";
};
</script>

<template>
  <div class="img-container">
    <img
      v-for="index in 9"
      :key="index"
      class="beer"
      :alt="currentBeer.toString()"
      :src="chooseBeerImage(index)"
    />
  </div>
</template>

<style scoped>
.img-container {
  display: flex;
  justify-content: space-between;
}

img.beer {
  width: 60px;
}

@media (max-width: 1250px) {
  img.beer {
    width: 40px;
  }
}
</style>
