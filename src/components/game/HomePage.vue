<template>
  <div class="home-page flex-column flex-center">
    <div v-if="sessionUUID">
      <div>{{ gameResultMessage }}</div>
      <button @click="resetGame">Play again</button>
    </div>

    <div v-else>
      <div class="title">
        ROCK – PAPER – SCISSORS
      </div>

      <div class="choices flex-row gap-10">
        <img src="@/assets/rock.svg" @click="play('rock')"/>
        <img src="@/assets/paper.svg" @click="play('paper')"/>
        <img src="@/assets/scissors.svg" @click="play('scissors')"/>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import axios from 'axios'

const sessionUUID = ref(localStorage.getItem('uuid'))
const gameResultMessage = ref('')

const play = async (choice) => {
  sessionUUID.value = sessionUUID.value || crypto.randomUUID()
  const parameters = {
    uuid: sessionUUID.value,
    game: { user_choice: choice }
  }

  const { status, data } = await axios.post('http://localhost:3000/games/create-or-show', parameters)
  
  if (status === 200 || status === 201) {
    gameResultMessage.value = data.result
    localStorage.setItem('uuid', sessionUUID.value)
  } else {
    gameResultMessage.value = 'Something went wrong'
  }
}

const resetGame = () => {
  localStorage.removeItem('uuid')

  sessionUUID.value = null
  gameResultMessage.value = ''
}

onMounted(() => {
  if (sessionUUID.value) { play(null) }
})
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
  width: 150px;
  height: 150px;
}

.home-page .choices img:hover {
  background: #F2F2F2;
  border-radius: 5px;
}
</style>