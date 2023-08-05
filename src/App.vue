<script setup lang="ts">
</script>

<template>
  <div>
    <h1>final countdown</h1>
    <h2>(display time here)</h2>
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
        <button>Restart</button>
      </div>
  </div>
</template>

<style scoped>

.but-div {
  margin-top: 15px;
}

</style>
