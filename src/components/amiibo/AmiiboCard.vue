<template>
  <div class="amiibo-card">
    <img :src="amiibo.image" :alt="amiibo.name">
    <h3>{{ amiibo.name }}</h3>
    <p>Series: {{ amiibo.amiiboSeries }}</p>
    <p>Game Series: {{ amiibo.gameSeries }}</p>
  </div>
</template>

<script>
export default {
  name: 'AmiiboCard',
  props: {
    amiibo: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.amiibo-card {
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 16px;
  margin: 8px;
  text-align: center;
  max-width: 200px;
}

.amiibo-card img {
  width: 100%;
  height: auto;
  max-height: 200px;
  object-fit: contain;
}

.amiibo-card h3 {
  margin: 8px 0;
}

.amiibo-card p {
  color: #666;
  margin: 4px 0;
}
</style>
