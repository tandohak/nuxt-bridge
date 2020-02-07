<template>
  <div class="main-container">
    <div class="inner-content">
      <!-- # 로고  -->
      <div class="logo"></div>
      <div class="--text--middle text-content --bold--600">개발자, 디자이너, 기획자의 소통 공간. 브릿지</div>

      <!-- # 폼 시작 -->
      <form v-model="valid" class="form-sign-up" @submit.prevent="submit">
        <input type="email" :rules="emailRules" v-model="email" required="required" placeholder="이메일로 입력">
        <div v-if="isSendEmail" class="--text--micro message">임시 로그인 코드를 보냈습니다.</div>
        <input v-if="isSendEmail" :rules="codeRules" v-model="code" type="text" required="required" placeholder="임시 코드 입력">
        <button >{{buttonText[isSendEmail ? 1 : 0]}}</button>
      </form>
      <!-- # 폼 끝 -->
    </div>
  </div>
</template>

<script>
  export default {
    beforeMount() {
      // email 이 있을 경우 메일 센드
      if(this.email) {
        this.sendCode();
      }
    },
    data() {
      return {
          valid: false,
          buttonText: ['이메일 보내기', '로그인하기'],
          isSendEmail: false,
          code: null,
          emailRules: [
            v => !!v || '이메일은 필수입니다.',
            v => /.+@.+/.text(v) || '이메일이 유효하지 않습니다.'
          ],
          codeRules: [
            v => !!v || '코드를 입력해주세요.'
          ]
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
      submit() {
        if (!this.isSendEmail) {
          // 이메일 샌드 로직.
          this.sendCode();
        } else {
          // 코드 확인 로직
        }
      },
      sendCode() {
        this.isSendEmail = true;
      }
    }
  }
</script>

<style lang="sass">
  @import "assets/css/main.sass"

</style>
