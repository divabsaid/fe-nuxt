<template>
  <Dashboard />
</template>

<script>
export default {
  name: 'IndexPage',
  middleware: 'isAuthenticated'
  // computed: {
  //   isAuthenticated () {
  //     return this.$store.getters.isAuthenticated // it check if user isAuthenticated
  //   }
  // },
  // methods: {
  //   async logout () {
  //     await this.$auth.logout() // this method will logout the user and make token to false on the local storage of the user browser
  //   }
  // }
}
</script>
