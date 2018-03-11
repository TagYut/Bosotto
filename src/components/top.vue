<template>
  <div class="main-contents">
    <ul class="nav">
      <li class="nav-title">Yuesagashi/ゆえさがし</li>
      <li class="nav__text"><span class="nav__bigger">ゆ</span>えなきうた（らんだむに表示する）</li>
      <li class="nav__text"><span class="nav__bigger">さ</span>がす（詩をさがす）</li>
      <li class="nav__text"><span class="nav__bigger">う</span>たう（詩をかく）</li>
<!--      <li class="nav__text"><span class="nav__bigger">き</span>みたちのうた（ろぐいんする）</li> -->
    </ul>
    <div class="title">
      <h2 class="title__big-text"><span class="title__bigger">Y</span>UESAGASHI.</h2>
      <p class="title__text">ゆえさがしは登録制の短詩投稿サイトですよ。匿名でもよむことはできます。</p>
    </div>
    <div class="main">
      <div class="card"><p>中臣の 太祝詞言 言ひ祓へ 贖ふ命も 誰がために汝れ</p></div>
      <div class="card"><p>Without haste, but without rest.</p></div>
      <div class="card"><p>Let's Do this!!</p></div>
      <div class="card" id="uta01"></div>
      <button id="button">Test</button>
    </div>
  </div>
</template>

<script src="https://www.gstatic.com/firebasejs/4.1.3/firebase.js"></script>
<script>
import Vue from 'vue'
import * as firebase from 'firebase'
// Initialize Firebase
var config = {
  apiKey: 'AIzaSyDgejenkaYCik4LPmeLe3I5CNwuCH6rVak',
  authDomain: 'firevue-test-412cb.firebaseapp.com',
  databaseURL: 'https://firevue-test-412cb.firebaseio.com',
  projectId: 'firevue-test-412cb',
  storageBucket: 'firevue-test-412cb.appspot.com',
  messagingSenderId: '23707998568'
}
firebase.initializeApp(config)

var database = firebase.database()
var dataRef = database.ref('/uta-data')
  dataRef.on ('value',function (snapshot) {
      document.getElementById("button").onclick = function() {
        document.getElementById('uta01').innerHTML = snapshot.child('uta01').val()
      }
    })

export default {

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  @import url(https://fonts.googleapis.com/earlyaccess/sawarabimincho.css);
  .wf-sawarabimincho { font-family: "Sawarabi Mincho"; }

  .main-contents {
    --color: whitesmoke;
    margin: 0 5% 0 5%;
    padding: 0 5% 0 5%;
  }
  .nav {
    position: absolute;
    height: 25px;
    width: 80%;
    color: var(--color);
    background: black;
    font-family: 'Yu Gothic','MS Gothic';
    font-weight: bold;
    font-size: 0.9rem;
    text-align: left;
  }
  .nav-title {
    margin-left: 5px;
    text-align: left;
    font-size: 1rem;
    display: inline-block;
  }
  .nav__text {
    margin-left: 5%;
    text-align: right;
    display: inline-block;
  }
  .nav__bigger {
    font-size: 1rem;
  }
  .title__bigger {
    font-size: 3rem;
  }
  .title {
    text-align: left;
  }
  .title__big-text {
    font-size: 2rem;
  }
  .title__text {
    height: 20px;
    font-size: 1rem;
    font-family: 'Yu Gothic','MS Gothic';
    color: var(--color);
    background: black;
  }
  .card {
    text-align: left;
    font-family: "Sawarabi Mincho";
    font-weight: bold;
    border:double 1px black;
  }
</style>
