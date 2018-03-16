<template>
  <div class="main">
    <div class="slope">
      <div class="slope__reverse" id="point">
        <h1 class="bosotto anim" v-bind:style="{ margin: hei + 'vh' }">{{ cry }}<i class="material-icons label">thumb_up</i></h1>
        <div class="slope__big-text">
          <h1>Bosotto it.</h1>
        </div>
        <div class="slope__text-box">
          <h2 class="slope__text">想いはあるか？幸せを知りたいか？生きる辛さを覚えているか？であれば朗報だ。おまえの辛さは変わらない。幸せにもならない。だが、想いはここで吐き出していけ。さあ、勇気を出して。おまえの想いは保存され、知らぬ誰かがそれを読む。そしてきっと、また想う。ぼそっとな。</h2>
          <p class="counter">{{ 31-count.length }}字</p>
          <input v-model.trim='count' maxlength='31' placeholder='つづる言葉はシンプルに' autofocus id="bosotto-input"><br>
          <button class="goto-bosott" @click="boso(); + plus();">ぼそっと呟く<i class="material-icons click">play_for_work</i></button>
          <p class="foot">© 2018 Bosottit.com</p>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import * as firebase from 'firebase'

export default {
  data () {
    return {
      count: '',
      anim: false,
      cry: 'この文章がちょうど30文字という確証はないがたぶんそうだろう',
      hei: (Math.floor(Math.random() * 76) + 5),
      Vue: require('vue'),
      firebase: require('firebase'),
      Vuefire: require('vuefire')
    }
  },
  methods: {
    boso () {
      let sakebi = document.getElementById('bosotto-input').value
      console.log(sakebi)
      firebase.database().ref('/data/sakebi').push(sakebi)
      // デバッグ用記述。リリース時に消す
      this.cry = sakebi
    },
    plus () {
      console.log('yatta!')
    // 作成途中。クリックするとanimationさせたい
    // let test = document.getElementById('point')
    // test.classList.add('anim')
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import url('https://fonts.googleapis.com/css?family=Bitter');
@import url('https://fonts.googleapis.com/icon?family=Material+Icons');

.label {
  padding-left: 5px;
  font-size: 36px;
  vertical-align: -5px;
}
.bosotto {
  z-index: 10;
  margin-top: 1vh;
 // padding-left: 300vw;
  position: absolute;
  white-space:nowrap;
  font-size: 25px;
  font-family: 'Yu Gothic','YuGothic',sans-serif;
  font-weight: bold;
  // 被ってボタン押せないので当たり判定なくすやつ
  pointer-events: none;
}
.anim {
  padding-left: 0;
  // こっからアニメーション処理
  animation-name: bosotto;
  animation-duration: 6s;
  animation-timing-function: linear;
  animation-fill-mode: forwards;
  @keyframes bosotto {
    from{ transform: translate(200vw, 0); }
    to{ transform: translate(-300vw, 0); }
  }
  @media screen and (min-width: 600px) {
    animation-duration: 10s;
    @keyframes bosotto {
    from{ transform: translate(100vw, 0); }
    to{ transform: translate(-200vw, 0); }
  }
  }
}
.counter {
  height: 2.5rem;
  position: absolute;
  transform: rotate(-15deg);
  display: inline-block;
  margin:-2.5vh -7vw -1vh;
  font-size: 1.9rem;
  @media screen and (min-width: 600px) {
  font-size: 2.3rem;
  margin: 0 -2.8vw -1vh;
  }
  &::first-letter{
    font-size: 2.5rem;
  @media screen and (min-width: 600px) {
  font-size: 3.6rem;
  }
  }
}
#bosotto-input {
  margin: 1vh 0 1vh 0;
  font-size: 20px;
  font-family: 'Yu Gothic','YuGothic',sans-serif;
  font-weight: bold;
  background: whitesmoke;
  border: double 1px grey;
  transform: rotate(-2deg);
  @media screen and (min-width: 600px) {
    font-size:35px;
    margin-top: 3vh;
  }
}
.main {
  user-select: none;
  cursor: default;
  text-align: center;
  overflow: hidden;
  margin: 5vh 5px 5vh 10px;
}
.slope {
  border: dotted 1vh gold;
  height: 88vh;
  position: relative;
  color: gold;
  background: black;
  transform: rotate(5deg);
  &__reverse {
    transform: rotate(-4deg);
    line-height: 5vh;
  }
  &__text {
    font-size: 18px;
    max-width: 830px;
    @media screen and (min-width: 600px) {
      font-size: 28px;
      margin: auto;
      padding-top: 5vh;
    }
  }
  &__big-text {
    margin-right: 50px;
    padding-top: 1vh;
    transform: rotate(-1deg);
    font-family: 'Bitter', 'Trebuchet MS', serif;
    font-size: 25px;
    text-decoration: underline gold;
    @media screen and (min-width: 600px) {
      font-size: 40px;
    }
  }
  &__text-box {
    padding-left: 5vw;
    transform: rotate(1deg);
    width: 85vw;
  &:first-letter {
    font-size: 2em;
  }
  }
  .goto-bosott {
    cursor: pointer;
    padding-bottom: 1vh;
    background: rgba(0,0,0,0);;
    color: gold;
    border-style: none;
    font-family: 'Yu Gothic', 'YuGothic','Yu Gothic',serif;
    font-size: 2rem;
    font-weight: bold;
    transform: rotate(-4deg);
    @media screen and (min-width: 600px) {
      font-size: 3rem;
    }
  }
  .click {
    font-size: 60px;
    margin-left: -10px;
    vertical-align: -15px;
    @media screen and (min-width: 600px) {
      font-size: 80px;
      vertical-align: -20px;
    }
  }
  .foot {
    transform: rotate(-2deg);
    margin: -15px;
    @media screen and (min-width: 600px) {
      font-size: 20px;
    }
  }
}
</style>
