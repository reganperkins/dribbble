<template>
  <section :class="['auth-layout', classProp]">
    <span class="sign-in"
      >Already a member? <a href="#" class="link">Sign In</a></span
    >
    <main>
      <a herf="https://dribbble.com" class="sm-logo">
        <SVGLogo />
      </a>
      <h1>Sign up to Dribbble</h1>
      <SocialAuthButtons />

      <hr class="or-separator" />

      <slot></slot>
    </main>
  </section>
</template>

<script>
import SocialAuthButtons from "./SocialAuthButtons";
import SVGLogo from "../assets/svg-components/dribbble-logo.vue";

export default {
  name: "SignUp",
  props: {
    classProp: String
  },
  components: {
    SocialAuthButtons,
    SVGLogo
  },
  data: function() {
    return {
      errors: [],
      name: null,
      username: null,
      email: null,
      password: null,
      acceptedTerms: null,
      attemptSubmit: false,
      formError: false
    };
  }
};
</script>

<style lang="scss" scoped>
@import "src/styles/_variables.scss";

.auth-layout {
  display: flex;
  flex-direction: column;
  padding: 48px 24px;
  .sign-in {
    text-align: right;
    font-size: 14px;
    font-weight: 200;
  }
  main {
    max-width: 418px;
    align-self: center;
    flex-grow: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  .sm-logo {
    display: none;
  }
  @media (max-width: 1028px) {
    .sign-in {
      order: 1;
      text-align: center;
    }
    .sm-logo {
      display: block;
      svg {
        fill: $font-color;
      }
    }
  }
}
</style>
