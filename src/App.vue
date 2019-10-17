<template>
  <div>
    <button @click="setShowModal(true)">Create Account</button>
    <Modal v-if="showModal">
      <SignUp />
    </Modal>
  </div>
</template>

<script>
/*eslint no-console: ["error", { allow: ["warn"] }] */
import Modal from "./components/Modal.vue";
import SignUp from "./views/SignUp.vue";

export default {
  name: "app",
  components: {
    Modal,
    SignUp
  },
  data() {
    return {
      showModal: false,
    }
  },
  methods: {
    setShowModal: function(bool) {
      this.showModal = bool;
    }
  }
};
</script>

<style lang="scss">
#app {
  font-family: "Haas Grot Text R", Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
