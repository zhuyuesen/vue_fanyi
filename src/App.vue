<template>
  <div id="app">
    <h1>在线翻译</h1>
    <h5 style="color: #888;">简单 / 易用 / 便捷</h5>
    <transform v-on:formSubmit="translate"></transform>
    <transout v-text="translated"></transout>
  </div>
</template>

<script>
import Transform from './components/Transform'
import Transout from './components/Transout'

export default {
  name: 'app',
  data:function () {
    return{
      translated:''
    }
  },
  components: {
    Transform,Transout
  },
  methods:{
    translate:function (text,lang) {
//      console.log('事件传递');
//      console.log(text);
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20171019T173433Z.b67fa31ff42d01ad.c9704221dc7eeb05116fe5ee81102fa96f5a142c&lang='+lang+'&text='+text)
              .then((response)=>{
//        console.log(response.body.text[0]);
        this.translated = response.body.text[0];
      })
    }
  }
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
