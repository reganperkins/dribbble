<template>
  <section :class="['sign-up', classProp]">
      <span class="sign-in">Already a member? <a href="" class="link">Sign In</a></span>
      <main>
        <div class="sign-up-wrapper">
          <h1>Sign up to Dribbble</h1>
          <div class="button--row">
            <a class="google--button">Sign up with Google</a>
            <a class="twitter-icon--button">Twitter</a>
            <a class="facebook-icon--button">Facebook</a>
          </div>

          <hr class="or--separator" />

          <form>
            <div class="form-group">
              <fieldset>
                <label for="fullname">Full Name</label>
                <input name="fullname" id="fullname" type="text" />
              </fieldset>

              <fieldset>
                <label for="username">Username</label>
                <input name="username" id="username" type="text" />
              </fieldset>
            </div>

            <div class="form-group">
              <fieldset>
                <label for="email">Email Address</label>
                <input name="email" id="email" type="email" />
              </fieldset>
            </div>

            <div class="form-group">
              <fieldset>
                <label for="password">Password</label>
                <input name="password" id="password" type="password" placeholder="6+ characters"/>
              </fieldset>
            </div>

            <div class="form-group">
              <fieldset>
                <div class="checkbox-wrapper">
                  <input name="terms-agreement" id="terms-agreement" type="checkbox" class="terms-agreement-checkbox"/>
                  <label for="terms-agreement" class="terms-agreement">Creating an account means you’re okay with our <a class="link" target="_blank" href="https://dribbble.com/terms">Terms of Service</a>, <a class="link" target="_blank" href="https://dribbble.com/privacy">Privacy Policy</a>, and our default <a class="link" target="_blank" href="https://dribbble.com/notifications">Notification Settings</a>.</label>
                </div>
              </fieldset>
            </div>
            <input type="submit" value="Create Account" class="standard--button submit-button" />
          </form>
        </div>
      </main>
    </section>
</template>

<script>
export default {
  name: "SignUp",
  props: {
    classProp: String
  }
};
</script>

<style lang="scss" scoped>
@import 'src/styles/_variables.scss';

.sign-up {
  display: flex;
  flex-direction: column;
  padding: 48px;
  overflow: auto;
  .sign-in {
    text-align: right;
    font-size: 14px;
  }
  .sign-up-wrapper {
    width: 418px;
    margin: 0 auto;
  }
  main {
    flex-grow: 1;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  fieldset {
    flex-grow: 1;
  }
  .terms-agreement {
    font-size: 14px;
    font-weight: initial;
    color: $grey;
  }
  .submit-button {
    margin: 20px 0;
  }
  .checkbox-wrapper {
    display: flex;
    > :nth-of-type(1) {
      margin-right: 8px;
    }
  }

}
</style>
