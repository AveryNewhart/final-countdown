<script setup lang="ts">
import { ref } from 'vue';

const startingTime = ref("hours" | "minutes" | "seconds");

// setting the state of which the time is
const state = ref<"stopped" | "running" | "paused">("stopped");

function Start() {

}

function Pause() {

}

function Reset() {

}

function formatTime(startingTime: number) {
  const hours = `0${Math.floor(startingTime / 24)}`.slice(-2);
  const minutes = `0${Math.floor(startingTime / 60)}`.slice(-2);
  const seconds = `0${startingTime % 60}`.slice(-2);
  return `${hours}:${minutes}:${seconds}`;
}

</script>

<template>
  <div>
    <h1>final countdown</h1>
    <h2>(display time here){{ formatTime(startingTime) }}</h2>
      <div>
        <label for="hours">Hour(s):</label>
        <input type="number" id="hours" min="0" max="24" />
        <label for="minutes">Minute(s):</label>
        <input type="number" id="minutes" min="0" max="60" />
        <label for="seconds">Second(s):</label>
        <input type="number" id="seconds" min="0" max="60" />
      </div>
      <div class="but-div">
        <button>Start</button>
        <button>Pause</button>
        <button>Reset</button>
      </div>
  </div>
</template>

<style scoped>

.but-div {
  margin-top: 15px;
}

</style>
