<template>
  <div class="main-container">
      <div class="inner-content">
        <!-- # 로고  -->
        <div class="logo"></div>
        <div class="--text--middle text-content --bold--600">개발자, 디자이너, 기획자의 소통 공간. 브릿지</div>
        <div class="--text--small sub-text-content">지금 바로 시작해보세요.</div>

        <!-- # 폼 시작 -->
        <form class="form" @submit.prevent="start">
          <input type="email" required="required" v-model="email" placeholder="이메일로 시작하기">
          <button type="submit">시작하기</button>
        </form>
        <!-- # 폼 끝 -->

      </div>
  </div>
</template>

<script>

export default {
  data() {
    return {
    }
  },
  computed: {
    email: {
      get () {
        return this.$store.state.email;
      },
      set (value) {
        this.$store.commit('setEmail', value);
      }
    }
  },
  methods: {
    start() {
      this.$router.push('/signup')
    }
  }
}
</script>

<style lang="sass">
  @import "assets/css/main.sass"

</style>
