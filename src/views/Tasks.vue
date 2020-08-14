<template>
  <div>
    <Toast v-show="this.content" :content="this.content"></Toast>
    <Tabs>
      <Tab name="Activities">
        <TaskList :activities="activities" header="All activities" v-on:finishedActivity="onFinishedActivity"></TaskList>
      </Tab>
      <Tab name="Completed Activities">
        <TaskList :activities="completedActivities" header="Completed activities" v-on:finishedActivity="onFinishedActivity"></TaskList>
      </Tab>
      <Tab name="Pending Activities">
        <TaskList :activities="pendingActivities" header="Pending activities" v-on:finishedActivity="onFinishedActivity"></TaskList>
      </Tab>
    </Tabs>
  </div>
</template>

<script>
import TaskList from '@/components/TaskList.vue'
import Tabs from '@/components/Tabs.vue'
import Tab from '@/components/Tab.vue'
import Toast from '@/components/Toast.vue'

export default {
  name: 'Tasks',
  components: {
    TaskList,
    Tabs,
    Tab,
    Toast
  },
  data () {
    return {
      activities: [
        {
          id: 1,
          title: 'Send message to Someone',
          contact_email: 'someone@email.com',
          done: false
        },
        {
          id: 2,
          title: 'Meeting with Anothaone',
          contact_email: 'anothaone@email.com',
          done: true
        },
        {
          id: 3,
          title: 'Call Itshimagain',
          contact_email: 'itshimagain@email.com',
          done: false
        },
        {
          id: 4,
          title: 'Remember bithday of Notsure',
          contact_email: 'notsure@email.com',
          done: true
        },
        {
          id: 5,
          title: 'Don"t forget meeting with Yepitshim',
          contact_email: 'yepitshim@email.com',
          done: false
        }
      ],
      content: []
    }
  },
  computed: {
    completedActivities () {
      return this.activities.filter(activity => activity.done)
    },
    pendingActivities () {
      return this.activities.filter(activity => !activity.done)
    }
  },
  methods: {
    onFinishedActivity (e) {
      this.content = {
        header: 'Activity Finished',
        body: 'The activity #' + e + ' was finished',
        show: true
      }
    }
  }
}
</script>
