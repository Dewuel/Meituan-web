<template>
  <div class="m-user">
    <template v-if="user">
      <span class="username">{{ user }}</span>
      <nuxt-link
        to="/exit"
        class="exit"
      >退出</nuxt-link>
    </template>
    <template v-else>
      <nuxt-link
        to="/login"
        class="login"
      >立即登录</nuxt-link>
      <nuxt-link
        class="register"
        to="/register"
      >注册</nuxt-link>
    </template>
  </div>
</template>

<script>
export default {
  data() {
    return {
      user: ""
    };
  },
  async mounted() {
    //get返回的是promise对象，最后可以用then
    const { status, data: { user } } = await this.$axios.get("/users/getUser");
    if (status === 200) { this.user = user; }
  }
};
</script>