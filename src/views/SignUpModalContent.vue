<template>
  <div id="sign-up-page">
    <FeaturePanel classProp="side-panel" textColor="#866211" />
    <SignUp classProp="sign-up-panel" :setShowModal="setShowModal" />
  </div>
</template>

<script>
import FeaturePanel from "../components/FeaturePanel.vue";
import SignUp from "../components/SignUp.vue";

export default {
  name: "SignUpModalContent",
  components: {
    FeaturePanel,
    SignUp
  },
  props: {
    setShowModal: Function
  }
};
</script>

<style lang="scss" scoped>
@import "src/styles/_variables.scss";

@media (max-width: 1028px) {
  .side-panel {
    display: none;
  }
}

#sign-up-page {
  display: flex;
  align-items: stretch;
  flex-grow: 1;
  min-height: 100%;
  background: $white;
}
.side-panel {
  flex-basis: 514px;
  flex-grow: 0;
  flex-shrink: 0;
  background: $yellow-gradient;
}
.sign-up-panel {
  flex-grow: 1;
}
</style>
