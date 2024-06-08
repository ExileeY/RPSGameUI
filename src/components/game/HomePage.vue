<template>
  <div class="home-page flex-column flex-center">
    <div class="title">
      ROCK – PAPER – SCISSORS
    </div>

    <div class="choices flex-row gap-10">
      <div @click="play('rock')">
        1
      </div>

      <div @click="play('paper')">
        2
      </div>

      <div @click="play('scissors')">
        3
      </div>
    </div>
  </div>
</template>

<script setup>
const play = (choice) => {
  console.log('userChoise:', choice)
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:ital,wght@0,100..900;1,100..900&display=swap');

.home-page {
  width: 100%;
  height: 100%;
  font-weight: normal;
  font-style: normal;
}

.home-page .title {
  font-family: 'Montserrat', sans-serif;
  font-size: 45px;
  text-align: left;
  line-height: 60px;
  color: #36006C;
}
</style>