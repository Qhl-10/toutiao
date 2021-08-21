<template>
<div class="login">
        <el-card class="login-card">
            <di class="title">
                <img src="../../assets/img/logo_index.png" alt="">
            </di>
            <el-form ref="loginForm" :model="loginForm" :rules="loginRules" style="margin-top: 20px">
                <el-form-item prop="mobile">
                    <el-input v-model="loginForm.mobile" placeholder="请输入手机号"></el-input>
                </el-form-item>
                <el-form-item prop="code">
                    <el-input v-model="loginForm.code" style="width: 60%" placeholder="请输入验证码"></el-input>
                    <el-button style="float: right" plain>发送验证码</el-button>
                </el-form-item>
                <el-form-item prop="checked">
                    <el-checkbox v-model="loginForm.checked">我已阅读同意用户协议的隐私</el-checkbox>
                </el-form-item>
                <el-form-item>
                    <el-button @click="login" style="width: 100%" type="primary">登录</el-button>
                </el-form-item>
            </el-form>
        </el-card>
    </div>
</template>

<script>
export default {
  data () {
    return {
      loginForm: {
        mobile: '',
        code: '',
        checked: false
      },
      loginRules: {
        mobile: [{ required: true, message: '您的手机号不能为空' }, { pattern: /^1[3-9]\d{9}$/, message: '您的手机号格式不正确' }],
        code: [{ required: true, message: '您的验证码不能为空' }, { pattern: /^\d{6}$/, message: '验证码应该是六位数字' }],
        checked: [{ validator: function (rule, value, callback) { value ? callback() : callback(new Error('您必须先同意用户隐私协议')) } }]
      }
    }
  },
  methods: {
    login () {
      this.$refs.loginForm.validate().then(() => {
        this.$axios({
          url: 'http://127.0.0.1:5000/login',
          data: this.loginForm,
          method: 'post'
        }).then(res => {
          console.log(res)
          this.$router.push('/home')
          this.$message({
            message: '登录成功',
            type: 'success'
          })
        }).catch(err => {
          console.log('登录失败', err)
          this.$message.error({
            message: '手机号或者验证码错误',
            type: 'warning'
          })
        })
      })
    }
  }
}
</script>

<style lang="less"  scoped>
    .login{
        background-image: url("../../assets/img/login_bg.jpg");
        height: 100vh;
        background-size: cover;
        display: flex;
        justify-content: center;
        align-items: center;
        .login-card{
            width: 440px;
            height: 340px;
            .title{
                display: block;
                text-align: center;
                img{
                    height: 40px;
                }
            }
        }
    }
</style>
