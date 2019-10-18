<template>
  <div id="sign-up-page">
    <FeaturePanel classProp="side-panel" textColor="#866211" /> 
    <SignUp classProp="sign-up-panel" />
  </div>
</template>

<script>

import FeaturePanel from "../components/FeaturePanel.vue";
import SignUp from "../components/SignUp.vue";

export default {
  name: "SignUpModalContent",
  components: {
    FeaturePanel,
    SignUp,
  },
};
</script>

<style lang="scss" scoped>
@import 'src/styles/_variables.scss';

#sign-up-page {
  display: flex;
  align-items: stretch;
  flex-grow: 1;
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