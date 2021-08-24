<template>
  <div>
    <p>this is message from API</p>
    <p>{{ rootMsg }}</p>
    <p>end</p>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'

export default Vue.extend({
  data() {
    return {
      rootMsg: 'default value of rootMsg',
    }
  },
  beforeMount() {
    console.log("========================")
    this.fetchSomething()
  },
  methods: {
    async fetchSomething() {
      const rootMsg = await this.$axios.$get(this.$config.apiBaseURL)
      this.rootMsg = rootMsg
    },
  },
})
</script>
