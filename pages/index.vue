<script setup>
import MainTitle from "~/components/MainTitle.vue";
import CountDown from "~/components/CountDown.vue";
</script>

<template>
  <div>
    <img class="back" alt="Dijon" src="/assets/back.jpeg" />
    <div class="content">
      <img alt="Marmelab logo" class="logo" src="/assets/logo-green.png" />
      <MainTitle message="Forbach, nous voici !!!" class="title" />
      <CountDown
        start="2025-04-28T09:00:00.000Z"
        deadline="2025-05-21T15:20:00.000Z"
      />
    </div>
    <!-- <nuxt-link to="/about">Go to About Page</nuxt-link> -->
  </div>
</template>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  padding-top: 60px;
}

@media (max-width: 1250px) {
  #app {
    padding-top: 10px;
  }
}

.back {
  width: calc(100% - 60px);
  margin: 30px;
  position: absolute;
  top: 0;
  left: 0;
  filter: contrast(40%) blur(5px) brightness(1.5);
}

@media (max-width: 1250px) {
  .back {
    margin: -10px;
    height: calc(100% + 20px);
    width: unset;
  }
}

.content {
  position: relative;
}

.content > .logo,
.content > .title {
  display: flex;
  margin: auto;
}

#greenframe_embedable_score_page {
  position: absolute;
  bottom: 10px;
  right: 40px;
}
</style>
