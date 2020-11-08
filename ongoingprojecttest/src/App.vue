<template>
  <tableView/>
</template>

<script>
import tableView from './components/tableView.vue'

export default {
  name: 'App',
  components: {
    tableView
  }
}
</script>

<style>
#app {
position: relative;
    width:95%;
    margin: auto;
    box-shadow: -3px 0px 5px -3px rgba(40,57,75, .5);
  border-top-left-radius: .5rem;
}
</style>
