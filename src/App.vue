<template>
  <div>
    <router-view/>
  </div>
</template>

<script>
export default {
  name: 'App'
}
</script>

<style>
  @import url(http://yui.yahooapis.com/3.18.1/build/cssreset/cssreset-min.css);
  @import url(https://fonts.googleapis.com/icon?family=Material+Icons);
  @import url(https://fonts.googleapis.com/css?family=Rammetto+One);
  @import url(https://fonts.googleapis.com/earlyaccess/mplus1p.css);

  .wf-mplus1p { font-family: "Mplus 1p"; }

  /* 以下のhtml2行はYahooのreset.cssを使った都合でこれを入れておかないと背景がおかしくなる */
  html {
    background-color: transparent;
    background-image: none;
  }

  body {
    background: whitesmoke;
    font-family: "Rammetto One","Mplus 1p", cursive;
    color: #000;
    font-size: 2rem;;
  }
</style>
