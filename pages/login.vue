<template>
  <div>
    <form
      method="post"
      @submit.prevent="login"
    >
      <input
        v-model="username"
        name="username"
        type="text"
        placeholder="Username"
      >
      <input
        v-model="password"
        name="password"
        type="password"
        placeholder="Password"
      >

      <button
        type="submit"
      >
        Login
      </button>
    </form>
  </div>
</template>

<script>
export default {
  name: 'LoginPage',
  data: () => ({
    username: '',
    password: ''
  }),
  methods: {
    async login () {
      try {
        const response = await this.$auth.loginWith('local', {
          data: {
            username: this.username,
            password: this.password
          }
        })

        this.$router.push('/')
        console.log(response)
      } catch (err) {
        console.log(err)
      }
    }
  }
}
</script>
