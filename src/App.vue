<template>
  <div id="app">
    <super-invested></super-invested>
  </div>
</template>

<script>
import SuperInvested from './components/SuperInvested'

export default {
  name: 'app',
  components: {
    SuperInvested
  }
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Open+Sans:400,600|Scope+One');
  @import './assets/styles/app.scss'
</style>
