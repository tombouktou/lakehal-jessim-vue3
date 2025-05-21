<!-- TableView.vue -->
<template>
  <div class="table-view">
    <h1>Amiibo Collection</h1>
    <AmiiboTable :amiibos="displayedAmiibos" />
    <div class="load-more" v-if="hasMoreAmiibos">
      <button @click="loadMore" :disabled="loading">
        {{ loading ? 'Loading...' : 'Load More' }}
      </button>
    </div>
  </div>
</template>

<script>
import { ref, onMounted } from 'vue'
import AmiiboTable from '@/components/amiibo/AmiiboTable.vue'

export default {
  name: 'TableView',
  components: {
    AmiiboTable
  },
  setup() {
    const allAmiibos = ref([])
    const displayedAmiibos = ref([])
    const loading = ref(false)
    const currentPage = ref(1)
    const itemsPerPage = 10
    const hasMoreAmiibos = ref(true)

    const fetchAmiibos = async () => {
      if (loading.value) return
      loading.value = true
      try {
        const response = await fetch('https://www.amiiboapi.com/api/amiibo/')
        const data = await response.json()
        allAmiibos.value = data.amiibo
        displayedAmiibos.value = allAmiibos.value.slice(0, itemsPerPage)
        hasMoreAmiibos.value = displayedAmiibos.value.length < allAmiibos.value.length
      } catch (error) {
        console.error('Error fetching amiibos:', error)
      } finally {
        loading.value = false
      }
    }

    const loadMore = () => {
      const nextItems = allAmiibos.value.slice(
        currentPage.value * itemsPerPage,
        (currentPage.value + 1) * itemsPerPage
      )
      displayedAmiibos.value = [...displayedAmiibos.value, ...nextItems]
      currentPage.value++
      hasMoreAmiibos.value = displayedAmiibos.value.length < allAmiibos.value.length
    }

    onMounted(() => {
      fetchAmiibos()
    })

    return {
      displayedAmiibos,
      loading,
      hasMoreAmiibos,
      loadMore
    }
  }
}
</script>

<style scoped>
.table-view {
  padding: 20px;
  max-width: 1200px;
  margin: 0 auto;
}

h1 {
  text-align: center;
  color: #2c3e50;
  margin-bottom: 2rem;
}

.load-more {
  text-align: center;
  margin: 2rem 0;
}

button {
  background-color: #42b883;
  color: white;
  border: none;
  padding: 12px 24px;
  border-radius: 4px;
  cursor: pointer;
  font-size: 1rem;
  transition: background-color 0.3s;
}

button:hover {
  background-color: #3aa876;
}

button:disabled {
  background-color: #cccccc;
  cursor: not-allowed;
}
</style>
