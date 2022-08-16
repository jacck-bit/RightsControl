<template>
  <div class="clearfix" id="login_wrap">
    <h2 class="title">登录页</h2>
    <div id="login">
      <div class="login--account">
        <span>账号：</span>
        <input type="text" placeholder="随便输" name="account" v-model.trim="account" />
      </div>
      <div class="login--password">
        <span>密码：</span>
        <input
          type="password"
          placeholder="随便输"
          name="password"
          v-model.trim="password"
          @keyup.enter="login"
        />
      </div>
      <p class="login--btn">
        <button id="loginBtn" @click="login">登录</button>
      </p>
    </div>
  </div>
</template>

<script>


export default {
  data() {
    return {
      account: "",
      password: ""
    };
  },
  methods: {
    async login() {
        // 网络请求
        let data = await login(this.account);
        let token = data.token;
        // 本地  vuex
        this.$store.commit('LOGIN_IN',token);
        this.$router.replace("/")
    }
  },
  mounted() {}
};
</script>
<style scoped lang="scss">

</style>
