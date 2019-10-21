<template>
  <div>
    <button @click="setShowModal(true)" class="center standard--button">
      Create Account
    </button>
    <Modal v-if="showModal">
      <SignUpModalContent />
    </Modal>
  </div>
</template>

<script>
import Modal from "./components/Modal.vue";
import SignUpModalContent from "./views/SignUpModalContent.vue";

export default {
  name: "app",
  components: {
    Modal,
    SignUpModalContent
  },
  data() {
    return {
      showModal: false
    };
  },
  methods: {
    setShowModal: function(bool) {
      this.showModal = bool;
    }
  }
};
</script>

<style lang="scss">
@import "src/styles/_reset.scss";
@import "src/styles/_shared.scss";
</style>
