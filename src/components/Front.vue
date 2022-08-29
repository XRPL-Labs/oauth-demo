<template>
  <div>
      <h3 v-if="address">Signed in with: {{ address }}</h3>
      <button v-else @click="login()">
        Login
      </button>
      
      <div v-if="address">
        <h3> Sign A transaction with Xumm</h3>
        <button @click="sign()">
          Sign TXJSON
        </button>
      </div>
  </div>
</template>

<script>
import { XummPkce } from 'xumm-oauth2-pkce'

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
      console.log('I\'m the login button!')

      const auth = new XummPkce('b3b3c81d-2fdd-43aa-9092-219f81d5edad')
      this.result = await auth.authorize()
      console.log('Scan result:', this.result)

      this.address = this.result.me.account
      this.token = this.result.jwt
    },
    async sign() {
      console.log('Here we send the Transaction to the Xumm app')

      const payload = {
        TransactionType: "Payment",
        Destination: "ra5nK24KXen9AHvsdFTKHSANinZseWnPcX",
        Amount: '100000'
      }

      try {
        
        const res = await fetch('https://xumm.app/api/v1/xapp-jwt/payload', {
          method: 'POST',
          headers: {
            'Content-Type': 'application/json',
            Authorization: `Bearer ${this.token}`
          },
          body: JSON.stringify({ txjson: payload })
        })

        console.log(res)
      } catch(e) {
        console.log('Error while sending payload', e)
      }
    }
  }
}
</script>

<style scoped>

</style>

