<template>
  <div  class="row" id="transform">
    <div class="col-md-6 col-md-offset-3">

    <form id="transf" class="well form-inline" v-on:submit="formSubmit">
      <input class="form-control" type="text" v-model="text" placeholder="输入要翻译的内容">
      <select class="form-control" name="" id="" v-model="lang">
        <option value="en">英语 English</option>
        <option value="ru">俄罗斯语 Russian</option>
        <option value="ko">韩语 Korean</option>
        <option value="fr">法语 French</option>
      </select>
      <input class="btn btn-primary" type="submit" value="翻译">
    </form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'transform',
  data () {
    return {
      text:'',
      lang:''
    }
  },
  methods:{
    formSubmit:function (e) {
      e.preventDefault();
//      console.log('hello');
//      console.log(this.text);
      this.$emit('formSubmit',this.text,this.lang);
    }
  },
  created:function () {
    this.lang = 'en';
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#transf{
  border: 1px solid #eee;
  border-radius: 10px;
}
</style>
