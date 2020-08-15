<template>
  <div>
    <CreateTable :objects="objects" h1="Hop List"></CreateTable>
  </div>
</template>

<script>
import CreateTable from '../components/CreateTable'
import Axios from 'axios'

export default {
  name: 'Hops',
  components: {
    CreateTable
  },
  data () {
    return {
      objects: []
    }
  },
  created () {
    Axios.get('http://localhost:8000/api/hops').then(response => {
      this.objects = response.data
    })
  }
}
</script>

<style scoped>

</style>
