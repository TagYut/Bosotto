<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
import * as firebase from 'firebase'

var config = {
  apiKey: 'AIzaSyB9rbHYXMHuVa4kXx2Tq4wDr51e1NjEXUg',
  authDomain: 'yuesaga4.firebaseapp.com',
  databaseURL: 'https://yuesaga4.firebaseio.com',
  projectId: 'yuesaga4',
  storageBucket: 'yuesaga4.appspot.com',
  messagingSenderId: '688008551325'
}
firebase.initializeApp(config)

export default {
  name: 'App'
}
</script>

<style>
body {
  background: gold;
  color: black;
  font-family: 'serif','Yu Mincho', 'YuMincho', serif;
  font-size: 10px;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
