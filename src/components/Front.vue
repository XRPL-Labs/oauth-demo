<template>
  <div class="container">
    <div v-if="address">
      <small>STEP 1:</small>
      <h3>Signed in with:</h3>
      <code>{{ address }}</code>
    </div>
    <button v-else @click="login()" class="login">Login</button>

    <div v-if="address">
      <hr />
      <h3>
        <small>STEP 2:</small>
        Sign A transaction with Xumm
      </h3>
      <button @click="sign()" class="sign">Sign TXJSON</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'FrontPage',
  data() {
    return {
      result: null,
      address: null,
      token: null
    }
  },
  methods: {
    async login() {
      // Write your Xumm login logic here
      console.log("I'm the login button!")
    },
    async sign() {
      console.log('Here we send the Transaction to the Xumm app')
    }
  }
}
</script>

<style scoped></style>
