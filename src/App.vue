<template>
  <div id="app">
    <ResponsiveNavbar />
    <Table />
  </div>
</template>

<script>
import ResponsiveNavbar from '@/components/ResponsiveNavbar'
import Table from '@/components/Table'

export default {
  name: 'App',
  components: {
    ResponsiveNavbar, Table
  }
}
</script>

<style>
@import 'https://unpkg.com/ionicons@4.2.2/dist/css/ionicons.min.css';

body {
  overflow-y:hidden;
  margin: 0px;
}

#app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    Oxygen-Sans, Ubuntu, Cantarell, "Helvetica Neue", Helvetica, Arial,
    sans-serif;
}
</style>
