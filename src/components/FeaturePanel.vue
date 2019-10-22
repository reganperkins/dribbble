<template>
  <section :class="['feature-panel', classProp]" :style="{ color: textColor }">
    <div class="text-container">
      <a herf="https://dribbble.com" class="sm-logo">
        <SVGLogo :style="{ fill: textColor }" />
      </a>
      <h2>{{ title }}</h2>
    </div>
    <div class="image-container">
      <div
        class="feature-image"
        :style="{
          color: '#000000',
          backgroundImage: `url(${require(`../assets/images/${featureImage}`)})`
        }"
      ></div>
    </div>
    <p class="image-credit">
      Art by
      <a :href="featureImageLink" target="_blank">{{ featureImageCredit }}</a>
    </p>
  </section>
</template>

<script>
import SVGLogo from "../assets/svg-components/dribbble-logo.vue";

export default {
  name: "FeaturePanel",
  components: {
    SVGLogo
  },
  props: {
    classProp: String,
    textColor: String,
    title: {
      type: String,
      default: "Discover the world’s top Designers & Creatives."
    },
    featureImage: {
      type: String,
      default: "dribbble-web-illustrations-peter-tarka.png"
    },
    featureImageCredit: {
      type: String,
      default: "Peter Tarka"
    },
    featureImageLink: {
      type: String,
      default: "https://dribbble.com/shots/6592185-Web-Illustrations"
    }
  }
};
</script>

<style lang="scss" scoped>
@import "src/styles/_variables.scss";
h2 {
  line-height: 38px;
}
.feature-panel {
  display: flex;
  flex-direction: column;

  align-items: stretch;
  flex-grow: 1;
}
.text-container {
  padding: 56px 123px 0 64px;
}
.image-credit {
  padding: 22px 56px 32px;
}
.image-container {
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  flex: 1;
}
.feature-image {
  flex-grow: 1;
  width: 514px;
  max-height: 544px;
  min-height: 460px;
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
}
</style>
