<template>
  <div id="app">
    <h1>Google Authentication</h1>
    <ol>
      <li>npm i vue-google-signin-button-directive --save</li>
      <li>npm i axios --save</li>
      <li>Get a client ID from Google developer's console.</li>
      <li>If you succeed in getting idToken from Google, you can run a PHP file at <i>auth.hwaryong.com</i> with axios.</li>
      <li>If you apply this procedure to your app, you had better use PHP session.</li>
    </ol>
    <button v-google-signin-button="clientID" class="login-button">Continue with Google</button>
    <div id="output"></div>
  </div>
</template>
 
<script>
import GoogleSignInButton from 'vue-google-signin-button-directive'
import axios from 'axios'
let clientID = '100854524431-dgt3uc9jegi9245mr5hmgq18n30oevd1.apps.googleusercontent.com'
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