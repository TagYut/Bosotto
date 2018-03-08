<template>
  <div id="app">
    <img src="./assets/logo.png">
    <router-view/>
  </div>
</template>

<script src="https://www.gstatic.com/firebasejs/4.10.1/firebase.js"></script>
<script>

  var Vue = require('vue')
  var VueFire = require('vuefire')
  var firebase = require('firebase')

  // explicit installation required in module environments
  Vue.use(VueFire)

  var config = {
    apiKey: "AIzaSyDgejenkaYCik4LPmeLe3I5CNwuCH6rVak",
    authDomain: "firevue-test-412cb.firebaseapp.com",
    databaseURL: "https://firevue-test-412cb.firebaseio.com",
    projectId: "firevue-test-412cb",
    storageBucket: "firevue-test-412cb.appspot.com",
    messagingSenderId: "23707998568"
  }

  firebase.initializeApp(config)

export default {
  name: 'App'
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
