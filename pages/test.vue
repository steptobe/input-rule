<template>
  <div class="login-main">
    <div class="login-form">
      <div class="login-content">
        <div class="input_item">
          <label for="email">test1:</label>
          <input class="mt-input" name="testinput" type="text" id="email" v-bind:class="{'mt-valdate__error':errors.has('test4')}"   v-validate data-rules= "required range|1|100"  validate-name="test4" validate-type="change" validate-tips-required="请输入"  validate-tips-range="范围{0}到{1}">
          <span v-if="errors.has('test4')">{{errors.get('test4').msg}}</span>
        </div>
        <div class="input_item">
          <label for="email">test2:</label>
          <input class="mt-input" v-bind:class="{'mt-valdate__error':errors.has('test3')}"  type="text" id="email1"   v-validate:test3.change="validateTest"  >
          <span v-if="errors.has('test3')" >{{errors.get('test3').msg}}</span>
        </div>
        <div class="input_item">
          <label for="email">test3:</label>
          <input class="mt-input"  v-bind:class="{'mt-valdate__error':errors.has('test2')}" type="text" id="email2"   v-validate data-rules= "required"  validate-name="test2">
          <span v-if="errors.has('test2')" >{{errors.get('test2').msg}}</span>
  </div>
  <div class="input_item">
    <label for="email">test4:</label>
    <input class="mt-input" v-bind:class="{'mt-valdate__error':errors.has('test1')}"  type="text" id="email3"    v-validate:test1.input data-rules= "required min|100" >
    <span v-if="errors.has('test1')" >{{errors.get('test1').msg}}</span>
  </div>
  <input type="submit" class="login-btn" value="验证"  @click="check();">
  <input type="submit" class="login-btn" value="清除"  @click="clearAll();">
  </div>
  </div>
  </div>
</template>
<script>
  export default {
    name: 'login',
    data () {
      return {
        email: '',
        validateTest: {
          rules:{
            required:true,
            rangelength: [6,9]
          },
          msg:{
            required:"请输入",
            rangelength:'长度不超过{0}到{1}'
          }
        },
        password: '',
        validatePassword: [
          {required: '', msg: ""},
          {limit: this.limit, msg: ""}
        ]
      }
    },
    methods: {
      check: function () {
        let ret=this.$validator.checkAll();
        console.log(ret);
      },
      clearAll:function(){
        this.$validator.clear();
      }
    }
  }
</script>
