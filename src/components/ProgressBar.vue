<template>
  <div>
    <div class="title">
      {{ props.title }}
    </div>
    <div class="container">
      <div class="percent">
        {{ props.progress }}%
      </div>
      <div class="bar">
        <div
          class="progress"
          :class="progressColor()"
          :style="`width: ${props.progress}%`"
        ></div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { defineProps } from "vue";

const props = defineProps({
  title: { 
    type: String,
    default: 'Barre de progression',
  },
  progress: { 
    type: Number,
    default: 0,
  },
});

const progressColor = () => {
  if (props.progress > 75) return 'p75'
  else if (props.progress > 50) return 'p50'
  else if (props.progress > 25) return 'p25'
  else return 'p00'
};
</script>

<style lang="scss" scoped>
.title {
  font-size: 14px;
  margin-bottom: 10px;
}

.container {
  min-width: 100%;
  display: flex;
  align-items: center;
}
.percent {
  font-size: 20px;
  width: 50px;
}
.bar {
  background-color: #373737;
  height: 15px;
  box-shadow: 0px 3px 6px #00000029;
  flex-grow: 1;
}
.progress {
  background-color: #fff;
  height: 100%;
}
.p75 {
  background-color: #30DB63;
}
.p50 {
  background-color: #60E8B6;
}
.p25 {
  background-color: #60ADE8;
}
.p00 {
  background-color: #7160E8;
}
</style>
