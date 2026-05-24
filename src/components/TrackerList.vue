<template>
  <section class="tracker-section">
    <h2>Meine Tracker</h2>

    <p v-if="loading">Tracker werden geladen...</p>
    <p v-if="errorMessage" class="error">{{ errorMessage }}</p>

    <ul v-if="!loading && !errorMessage" class="tracker-list">
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
      trackers: [],
      loading: true,
      errorMessage: ''
    }
  },
  mounted() {
    fetch('https://trackdaily-backend.onrender.com/api/trackers')
      .then((response) => {
        if (!response.ok) {
          throw new Error('Backend konnte nicht geladen werden')
        }
        return response.json()
      })
      .then((data) => {
        this.trackers = data
      })
      .catch(() => {
        this.errorMessage = 'Tracker konnten nicht geladen werden.'
      })
      .finally(() => {
        this.loading = false
      })
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

.error {
  color: darkred;
}
</style>