<template>
  <main class="app">
    <h1>TrackDaily</h1>
    <p>Eine App zum Verfolgen täglicher Gewohnheiten und Aktivitäten.</p>

    <TrackerList />
  </main>
</template>

<script>
import TrackerList from './components/TrackerList.vue'

export default {
  name: 'App',
  components: {
    TrackerList
  }
}
</script>

<style scoped>
.app {
  max-width: 800px;
  margin: 40px auto;
  padding: 24px;
  font-family: Arial, sans-serif;
}

h1 {
  color: #2c3e50;
}
</style>