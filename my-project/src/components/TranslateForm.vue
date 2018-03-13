<template>
  <div id="translateForm">
    <div class="form-horizontal">
    <form v-on:submit="formSubmit" id="transForm" >
      <textarea class="form-control" rows="4" placeholder="输入需要翻译的内容" v-model="textToTranslate"></textarea>
      <select v-model="language" class="form-control">
        <option value="en">英语English</option>
        <option value="ru">俄语Russian</option>
        <option value="ko">韩语Korean</option>
        <option value="ja">日语Janpenese</option>
        <option value="fr">法语French</option>
        <option value="zh">汉语Chinese</option>
        <option value="de">德语German</option>
        <option value="es">西班牙语Spanish</option>
        <option value="th">泰语Thai</option>
        <option value="it">意大利语Italian</option>
        <option value="pt">葡萄牙语Portuguese</option>
      </select>
      <input type="submit" value="翻译" class="btn btn-primary">
    </form>
    </div>
  </div>
</template>

<script>

export default {
  name: 'translateForm',
  data:function(){
    return {
      textToTranslate:"",    //通过v-model抓取输入数据
      language:""
    }
  },
  methods:{
    formSubmit:function(e){
      // alert(this.textToTranslate);  //显示抓取的输入数据
      this.$emit("formSubmit",this.textToTranslate,this.language);  
      e.preventDefault();    //不刷新当前页面
    }
  },
  created:function(){
    this.language = "en";
  }
}
</script>

<style>
  #transForm{
    border-radius: 10px;
    border: 1px #ccc soild;
  }
</style>
