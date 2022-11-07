<template>
  <div class="container">
    <div class="title">
      <p>
        Test technique WEB-ATRIO réalisé par GILLES Maxence
        <br />
        réalisé le 07/11/2022
      </p>
    </div>

    <div
      v-for="bar, index of barsMap"
      :key="index"
      class="bars"
    >
      <ProgressBar
        :title="bar.title"
        :progress="bar.progress"
      />
    </div>

    <div class="buttons">
      <button @click="setProgress()">
        <span>Remettre à zéro les compteurs</span>
      </button>
      <button @click="setProgress(5)">
        <span>Ajouter 5%</span>
      </button>
      <button @click="setProgress(10)">
        <span>Ajouter 10%</span>
      </button>
    </div>
  </div>
</template>

<script setup>
import ProgressBar from '@/components/ProgressBar.vue'

import { ref } from "vue";

const barsMap = ref([
  {
    title: 'Initialisation du test technique',
    progress: 50
  },
  {
    title: 'Avancement de la phase de développement',
    progress: 25
  },
]);

const setProgress = (prog) => {
  for (let bar of barsMap.value) {
    if (prog) {
      if ((bar.progress += prog) > 100) bar.progress = 100
    }
    else bar.progress = 0
  }
}
</script>

<style lang="scss" scoped>
.container {
  > * {
    margin: 80px;
  }
}

.title {
  text-align: center;
  font-weight: bold;
  font-size: 16px;
}

.bars {
  display: flex;
  flex-direction: column;
  max-width: 840px;
  margin: auto;
  > div {
    margin: 20px;
  }
}

.buttons {
  display: flex;
  justify-content: center;
}
button {
  cursor: pointer;
  background-color: #373737;
  border: none;
  box-shadow: 0px 3px 6px #00000029;
  font-size: 14px;
  padding: 10px;
  margin: 15px;
  color: currentColor;
}
</style>