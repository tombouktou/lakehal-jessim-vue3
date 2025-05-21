<template>
  <div class="home">
    <h1>Featured Amiibos</h1>
    <div class="amiibo-grid" v-if="randomAmiibos.length">
      <AmiiboCard 
        v-for="amiibo in randomAmiibos" 
        :key="amiibo.tail" 
        :amiibo="amiibo" 
      />
    </div>
    <div v-else class="loading">Loading...</div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue'
import AmiiboCard from '@/components/amiibo/AmiiboCard.vue'

export default {
  name: 'HomeView',
  components: {
    AmiiboCard
  },
  setup() {
    const randomAmiibos = ref([])

    const fetchRandomAmiibos = async () => {
      try {
        const response = await fetch('https://www.amiiboapi.com/api/amiibo/')
        const data = await response.json()
        const shuffled = data.amiibo.sort(() => 0.5 - Math.random())
        randomAmiibos.value = shuffled.slice(0, 3)
      } catch (error) {
        console.error('Error fetching amiibos:', error)
      }
    }

    onMounted(() => {
      fetchRandomAmiibos()
    })

    return {
      randomAmiibos
    }
  }
}
</script>

<style scoped>
.home {
  padding: 20px;
  max-width: 1200px;
  margin: 0 auto;
}

.amiibo-grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  gap: 20px;
  margin-top: 20px;
}

h1 {
  text-align: center;
  color: #2c3e50;
  margin-bottom: 2rem;
}

.loading {
  text-align: center;
  font-size: 1.2rem;
  color: #666;
  margin-top: 2rem;
}
</style>
