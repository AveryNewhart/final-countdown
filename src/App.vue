<script setup lang="ts">
import { ref, watch, computed } from 'vue';

const hours = ref(0);
const minutes = ref(0);
const seconds = ref(0);

// Combine hours, minutes, and seconds to calculate the starting time in seconds
const startingTime = computed(() => hours.value * 3600 + minutes.value * 60 + seconds.value);

// setting the state of which the time is
const state = ref<"stopped" | "running" | "paused">("stopped");

const interval = ref<number | undefined>(undefined);

function start() {
  state.value = "running";
  interval.value = setInterval(() => {
    startingTime.value--;
  }, 1000);
}

function pause() {

}

function reset() {

}

// Watch for changes in the startingTime, and reset the timer if it reaches 0
watch(startingTime, (newVal) => {
  if (newVal <= 0) {
    reset();
  }
});

function formatTime(timeInSeconds: number) {
  const hours = `0${Math.floor(timeInSeconds / 3600)}`.slice(-2);
  const minutes = `0${Math.floor((timeInSeconds % 3600) / 60)}`.slice(-2);
  const seconds = `0${timeInSeconds % 60}`.slice(-2);
  return `${hours}:${minutes}:${seconds}`;
}

</script>

<template>
  <div>
    <h1>Final Countdown</h1>
    <h2 v-if="state === 'running' || state === 'paused'">{{ formatTime(startingTime) }}</h2>
    <div>
      <label for="hours">Hour(s):</label>
      <input type="number" id="hours" v-model="hours" min="0" max="24" />
      <label for="minutes">Minute(s):</label>
      <input type="number" id="minutes" v-model="minutes" min="0" max="60" />
      <label for="seconds">Second(s):</label>
      <input type="number" id="seconds" v-model="seconds" min="0" max="60" />
    </div>
    <div class="but-div">
      <button v-if="state === 'stopped'" @click="start">Start</button>
      <button v-if="state === 'running'" @click="pause">Pause</button>
      <button v-if="state === 'paused'" @click="start">Resume</button>
      <button v-if="state === 'running' || state === 'paused'" @click="reset">Reset</button>
    </div>
  </div>
</template>


<style scoped>

.but-div {
  margin-top: 15px;
}

</style>
