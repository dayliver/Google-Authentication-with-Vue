# Google-Authentication-with-Vue
a demo Vue app which authenticates a Google user
## Getting Started
* Clone the source.
```
git clone https://github.com/dayliver/Google-Authentication-with-Vue
```
* Insert your Google cliend ID in App.vue in ./src.
```
import GoogleSignInButton from 'vue-google-signin-button-directive'
import axios from 'axios'
let clientID = 'YOUR GOOGLE CLIEND ID' // ← Here your cliend ID (Line #17)
export default {
```
* Change the destination URL.
```
axios
  .get('http://YOUR DESTINATION URL') // Change the URL (Line #30)
  .then(response => {
```
* Run the code.
```
npm run serve
```
* Connect to your local dev server with the URL
```
http://localhost:8080
```
### Prerequisites
You might need only one thing.
* [Vue CLI 3](https://cli.vuejs.org/) - Vue command line interface

## Built With
* [vue-google-signin-button](https://github.com/phanan/vue-google-signin-button) - It made my work extremely simple!
* [axios](https://github.com/axios/axios) - Don't say you don't know

## Notes
Every time you run the code, Vue Cli says something wrong. It comes from 'index.js' in vue-google-signin-button. You can easily change the code not to show the error message, but I don't want to touch the great work made by phanan, the vue-google-signin-button author.
