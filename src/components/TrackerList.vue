<template>
  <section class="tracker-section">
    <h2>Meine Tracker</h2>

    <ul class="tracker-list">
      <li v-for="tracker in trackers" :key="tracker.id" class="tracker-card">
        <h3>{{ tracker.name }}</h3>
        <p>Kategorie: {{ tracker.category }}</p>
      </li>
    </ul>
  </section>
</template>

<script>
export default {
  name: 'TrackerList',
  data() {
    return {
      trackers: [
        {
          id: 1,
          name: 'Lesen',
          category: 'Bildung'
        },
        {
          id: 2,
          name: '10.000 Schritte',
          category: 'Fitness'
        },
        {
          id: 3,
          name: 'Gym',
          category: 'Fitness'
        },
        {
          id: 4,
          name: 'Wasser trinken',
          category: 'Gesundheit'
        }
      ]
    }
  }
}
</script>

<style scoped>
.tracker-section {
  margin-top: 24px;
}

.tracker-list {
  list-style: none;
  padding: 0;
  display: grid;
  gap: 16px;
}

.tracker-card {
  padding: 16px;
  border-radius: 12px;
  background-color: #f4f4f4;
  border: 1px solid #ddd;
}

.tracker-card h3 {
  margin: 0 0 8px;
}

.tracker-card p {
  margin: 4px 0;
}
</style>