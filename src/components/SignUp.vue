<template>
  <form v-on:submit.prevent="signUp">
    <p v-if="this.formError" class="form-error">
      {{ this.formError }}
    </p>
    <div class="form-group">
      <fieldset :class="{ invalid: attemptSubmit && missingName }">
        <label for="fullname">Full Name</label>
        <input name="fullname" v-model="name" id="fullname" type="text" />
        <div class="error-message">Name is required</div>
      </fieldset>

      <fieldset :class="{ invalid: attemptSubmit && missingUsername }">
        <label for="username">Username</label>
        <input name="username" v-model="username" id="username" type="text" />
        <div class="error-message">Username is required</div>
      </fieldset>
    </div>

    <div class="form-group">
      <fieldset :class="{ invalid: attemptSubmit && missingEmail }">
        <label for="email">Email Address</label>
        <input name="email" v-model="email" id="email" type="email" />
        <div class="error-message">Email is required</div>
      </fieldset>
    </div>

    <div class="form-group">
      <fieldset
        :class="{
          invalid: attemptSubmit && (missingPassword || invalidPassword)
        }"
      >
        <label for="password">Password</label>
        <input
          name="password"
          v-model="password"
          id="password"
          type="password"
          placeholder="6+ characters"
        />
        <div class="error-message">Invalid Password</div>
      </fieldset>
    </div>

    <div class="form-group">
      <fieldset :class="{ invalid: attemptSubmit && missingTerms }">
        <div class="checkbox-wrapper">
          <input
            name="terms-agreement"
            v-model="acceptedTerms"
            id="terms-agreement"
            type="checkbox"
            class="terms-agreement-checkbox"
          />
          <label for="terms-agreement" class="terms-agreement"
            >Creating an account means you’re okay with our
            <a class="link" target="_blank" href="https://dribbble.com/terms"
              >Terms of Service</a
            >,
            <a class="link" target="_blank" href="https://dribbble.com/privacy"
              >Privacy Policy</a
            >, and our default
            <a
              class="link"
              target="_blank"
              href="https://dribbble.com/notifications"
              >Notification Settings</a
            >.</label
          >
        </div>
        <div class="error-message">Please agree to terms</div>
      </fieldset>
    </div>
    <input
      type="submit"
      value="Create Account"
      class="standard-button submit-button"
    />
  </form>
</template>

<script>
export default {
  name: "SignUp",
  props: {
    setShowModal: Function
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
  },
  computed: {
    missingName: function() {
      return !this.name;
    },
    missingUsername: function() {
      return !this.username;
    },
    missingEmail: function() {
      return !this.email;
    },
    invalidPassword: function() {
      return this.password.length < 5;
    },
    missingPassword: function() {
      return !this.password;
    },
    missingTerms: function() {
      return !this.acceptedTerms;
    }
  },
  methods: {
    formIsValid() {
      return (
        !this.missingName &&
        !this.missingUsername &&
        !this.missingEmail &&
        !this.invalidPassword &&
        !this.missingPassword &&
        !this.missingTerms
      );
    },
    async signUp() {
      this.attemptSubmit = true;
      this.formError = false;
      const { name, username, email, password } = this;

      if (this.formIsValid()) {
        try {
          const user = {
            fullname: name,
            username,
            email,
            password
          };
          let formData = new FormData();
          formData.append("user", user);

          const response = await fetch("http://polls.apiblueprint.org/signup", {
            method: "POST",
            mode: "no-cors",
            body: formData,
            headers: {
              "Content-type": "application/json;charset=utf-8"
            }
          });

          if (response.ok) {
            // const data = await response.json();
            this.setShowModal(false);
          } else {
            throw new Error(`HTTP error: ${response.status}`);
          }
        } catch (err) {
          /*eslint no-console: ["error", { allow: ["warn"] }] */
          console.warn(err);
          this.formError = "Ooops! There was a error processing your details.";
        }
      }
    }
  }
};
</script>

<style lang="scss" scoped>
@import "src/styles/_variables.scss";

fieldset {
  flex-grow: 1;
}
.terms-agreement {
  font-size: 14px;
  font-weight: 200;
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
.form-error {
  position: absolute;
  color: $pink;
  font-size: 12px;
}
@media (max-width: 1028px) {
  .submit-button {
    width: 100%;
  }
}
</style>
