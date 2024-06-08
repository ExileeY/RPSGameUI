<template>
  <div class="home-page flex-column flex-center">
    <div class="title">
      ROCK – PAPER – SCISSORS
    </div>

    <div class="choices flex-row gap-10">
      <img src="@/assets/rock.svg" @click="play('rock')"/>
      <img src="@/assets/paper.svg" @click="play('paper')"/>
      <img src="@/assets/scissors.svg" @click="play('scissors')"/>
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

.home-page .choices img {
  cursor: pointer;
  padding: 20px;
  width: 100px;
  height: 100px;
}

.home-page .choices img:hover {
  background: #F2F2F2;
  border-radius: 5px;
}
</style>