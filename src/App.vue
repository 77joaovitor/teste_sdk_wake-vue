<script setup>
async function login() {
      let query = `mutation customerAuthenticatedLogin($email: String!, $pass: String!) {
        customerAuthenticatedLogin(input: {input: $email, password: $pass}) {
          isMaster
          token
          legacyToken
          type
        }
      }`
      const sdkWake = window
      try {
        let response = await sdkWake.StoreFrontClientHook.query(query, {email: 'email', pass: 'pssword'})

        console.log('response', response)
      } catch (error) {
        console.log('error', error)
      }
    }

</script>

<template>
  <button @click="login()">Login</button>
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
