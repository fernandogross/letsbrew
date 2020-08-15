<template>
  <div class="container">
    <h1>{{ h1 }}</h1>
    <table class="table table-hover">
      <thead class="thead-dark">
      <tr>
        <th v-for="header in setupHeaders(objects)" :key="header">
          {{ header }}
        </th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="div in objects" :key="div">
        <td v-for="key in div" :key="key">{{ key }}</td>
      </tr>
      <tr v-if="!objects.length">
        <td colspan="4">No content found</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'CreateTable',
  props: {
    objects: Array,
    h1: String
  },
  data () {
    return {
      headers: []
    }
  },
  methods: {
    setupHeaders (objects) {
      objects.forEach(item => {
        this.headers = Object.keys(item)
      })
      return this.headers
    }
  }
}
</script>

<style scoped>
</style>
