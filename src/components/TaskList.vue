<template>
  <div class="container">
    <h1>{{ header }}</h1>
    <table class="table table-hover">
      <thead class="thead-dark">
      <tr>
        <th>Title</th>
        <th>Contact Email</th>
        <th>Status</th>
        <th>Action</th>
      </tr>
      </thead>
      <tbody>
      <tr v-for="activity in activities" :key="activity.title">
        <td>{{ activity.title }}</td>
        <td>{{ activity.contact_email }}</td>
        <td>{{ activity.done ? 'Completed' : 'Pending'}}</td>
        <td><button @click="manageActivity(activity)" class="btn btn-width btn-primary">{{ activity.done ? 'Reopen' : 'Finish'}}</button></td>
      </tr>
      <tr v-if="!activities.length">
        <td colspan="4">No activities found</td>
      </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: 'TaskList',
  props: {
    activities: Array,
    header: String
  },
  methods: {
    manageActivity (activity) {
      if (activity.done) {
        activity.done = false
      } else {
        activity.done = true
        this.$emit('finishedActivity', activity.id)
      }
    }
  }
}
</script>

<style scoped>
.btn-width {
  width: 100px;
}
</style>
