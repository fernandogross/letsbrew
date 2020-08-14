<template>
  <div :class="{ 'show': content.show }" class="toast top-right">
    <div class="toast-header">
      {{ content.header }}
      <button type="button" class="close pull-right" data-dismiss="toast" @click="content.show = false">&times;</button>
    </div>
    <div class="toast-body">
      {{ content.body }}
    </div>
  </div>
</template>

<script>
export default {
  name: 'Toast',
  props: {
    content: { required: true }
  },
  methods: {
    fadeToast () {
      setTimeout(() => {
        this.content.show = false
      }, 2000)
    }
  },
  updated () {
    if (this.content.show) {
      this.fadeToast()
    }
  }
}
</script>

<style scoped>
  .pull-right {
    position: absolute;
    top: 0;
    right: 0;
  }
  .top-right {
    position: absolute;
    top: 10px;
    right: 10px;
  }
</style>
