<template>
  <div>
    <form
      method="post"
      @submit.prevent="register"
    >
      <input
        v-model="username"
        name="username"
        type="text"
        placeholder="Username"
      >
      <input
        v-model="fullname"
        name="fullname"
        type="text"
        placeholder="Fullname"
      >
      <input
        v-model="email"
        name="email"
        type="email"
        placeholder="Email"
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
        Register
      </button>
    </form>
  </div>
</template>
<script>
export default {
  name: 'RegisterPage',
  data: () => ({
    username: '',
    fullname: '',
    email: '',
    password: ''
  }),
  methods: {
    async register () {
      try {
        const user = await this.$axios.$post('/api/v1/user/register', {
          fullname: this.fullname,
          email: this.email,
          password: this.password,
          username: this.username
        })
        console.log(user)
      } catch (err) {
        console.log(err)
      }
    }
  }
}
</script>
