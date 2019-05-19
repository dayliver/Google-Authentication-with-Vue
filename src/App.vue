<template>
  <div id="app">
    <h1>Google Authentication</h1>
    <ol>
      <li>npm i vue-google-signin-button-directive --save</li>
      <li>npm i axios --save</li>
      <li>Get a client ID from Google developer's console.</li>
    </ol>
    <button v-google-signin-button="clientID" class="login-button">Continue with Google</button>
    <div id="output"></div>
  </div>
</template>
 
<script>
import GoogleSignInButton from 'vue-google-signin-button-directive'
import axios from 'axios'
let clientID = 'YOUR GOOGLE CLIEND ID'
export default {
  directives: {
    GoogleSignInButton
  },
  data: () => ({
    clientID: clientID
  }),
  methods: {
    OnGoogleAuthSuccess (idToken) {
      console.log(idToken)
      let html = ''
      axios
        .get('http://auth.hwaryong.com')
        .then(response => {
          console.log(response)
          for(let key of Object.keys(response)){
            html += `<p>${key}: ${response[key]}</p>`
          }
          document.getElementById('output').innerHTML = html
        })
    },
    OnGoogleAuthFail (error) {
      console.log(error)
    }
  }
}
</script>

<style>
button.login-button {
  border: 0;
  padding: 20px;
  border-radius: 8px;
  background: crimson;
  color: white;
}
</style>