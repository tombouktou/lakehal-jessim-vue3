<template>
  <div class="amiibo-table">
    <table>
      <thead>
        <tr>
          <th>Image</th>
          <th>Name</th>
          <th>Series</th>
          <th>Game Series</th>
          <th>Release Date</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="amiibo in amiibos" :key="amiibo.tail">
          <td><img :src="amiibo.image" :alt="amiibo.name" class="table-image"></td>
          <td>{{ amiibo.name }}</td>
          <td>{{ amiibo.amiiboSeries }}</td>
          <td>{{ amiibo.gameSeries }}</td>
          <td>{{ amiibo.release?.na || 'TBA' }}</td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'AmiiboTable',
  props: {
    amiibos: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
.amiibo-table {
  width: 100%;
  overflow-x: auto;
}

table {
  width: 100%;
  border-collapse: collapse;
  margin: 16px 0;
}

th, td {
  padding: 12px;
  text-align: left;
  border-bottom: 1px solid #ddd;
}

th {
  background-color: #f5f5f5;
  font-weight: bold;
}

.table-image {
  width: 50px;
  height: 50px;
  object-fit: contain;
}

tr:hover {
  background-color: #f9f9f9;
}
</style>
