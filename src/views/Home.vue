<template lang="pug">
  .m-login
    .content
      .title
        .logo VUE SPA MS
      el-form.form(ref="form", :model="form", :rules="rules")
        el-form-item(prop="username")
          el-input(type="text", v-model="form.username", placeholder="请输入账户名", prefix-icon="iconfont icon-login-user", size="medium", @keyup.enter.native="login")
        el-form-item(prop="password")
          el-input(type="password", v-model="form.password", placeholder="请输入密码", prefix-icon="iconfont icon-login-pwd", size="medium", @keyup.enter.native="login")
        el-form-item
          el-button.btn-login(type="primary", @click="login", size="medium") 登录
</template>

<script>
  export default {
    name: 'login',
    data() {
      return {
      go: this.$route.query.go,
        form: {
          username: "admin",
          password: "123456"
        },
        rules:{
          username: [
            { required: true, message: '请输入账户名', trigger: 'blur' }
          ],
          password: [
            { required: true, message: '请输入密码', trigger: 'blur' }
          ]
        }
      }
    },
    async created(){

    },
    methods: {
      login() {
        this.$refs['form'].validate(async (valid) => {
          if (valid) {
            this.$router.push({path: this.go || '/about'});
          }
        });

      }
    }
  };
</script>

<style scoped>
  .m-login{ position: absolute; width: 100%; height: 100%; background: #CEE4EF;}
  .m-login .content{ position: absolute; width: 400px; left: 50%; margin-left: -200px; top: 15%;}
  .m-login .title{ padding-bottom: 60px;}
  .m-login .title .logo{ width: 370px; height: 150px; margin: 0 auto; background: #3bbc9c; overflow: hidden; text-indent: -88em;}
  .m-login .form{ background: rgba(255,255,255,.6); border-radius: 10px;  padding: 50px; box-shadow: 0 0 20px rgba(39,107,184,.5);}
  .m-login .form .btn-login{ width: 100%; font-size: 16px;}
</style>
