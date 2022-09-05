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
import {XummPkce} from 'xumm-oauth2-pkce'

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

      const auth = new XummPkce(/* insert public api key here **/)
      this.result = await auth.authorize()
      console.log('Scan result:', this.result)

      this.address = this.result.me.account
      this.token = this.result.jwt
    },
    async sign() {
      console.log('Here we send the Transaction to the Xumm app')

      const payload = {
        TransactionType: 'Payment',
        Destination: 'rJR4MQt2egH9AmibZ8Hu5yTKVuLPv1xumm',
        Amount: '1000000'
      }

      try {
        const res = await fetch('https://xumm.app/api/v1/xapp-jwt/payload', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
            Authorization: `Bearer ${this.token}`
          },
          body: JSON.stringify({txjson: payload})
        })

        console.log(res)
      } catch (e) {
        console.log('Error while sending payload', e)
      }
    }
  }
}
</script>

<style scoped></style>
