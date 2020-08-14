<template>
  <div>
    <ul class="nav nav-tabs" id="myTab" role="tablist">
      <li v-for="tab in tabs" :key="tab.name" class="nav-item">
        <a :class="{ 'active': tab.isActive }" @click="selectTab(tab)" class="nav-link" :id="makeId(tab.name)" :href="makeHref(tab.name)" data-toggle="tab" role="tab" aria-controls="home" aria-selected="true">
          {{ tab.name }}
        </a>
      </li>
    </ul>
    <div class="tab-pane fade show active" id="home" role="tabpanel" aria-labelledby="home-tab">
      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Tabs',
  props: {
    name: String
  },
  data () {
    return {
      tabs: []
    }
  },
  created () {
    this.tabs = this.$children
  },
  mounted () {
    this.tabs[0].isActive = true
  },
  methods: {
    makeId (tabName) {
      return tabName.toLowerCase().replace(/ /g, '-') + '-tab'
    },
    makeHref (tabName) {
      return '#' + tabName.toLocaleLowerCase().replace(/ /g, '-')
    },
    selectTab (selectedTab) {
      this.tabs.forEach(tab => {
        tab.isActive = (tab.name === selectedTab.name)
      })
    }
  }
}
</script>

<style scoped>

</style>
