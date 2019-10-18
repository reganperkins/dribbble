<template>
  <transition name="modal">
    <div class="modal center">
      <div class="container">
        <header v-if="$scopedSlots['header']">
          <slot name="header"></slot>
        </header>

        <slot></slot>
        
        <footer v-if="$scopedSlots['footer']">
          <slot name="footer"></slot>
        </footer>
      </div>
    </div>
  </transition>
  <!-- https://vuejs.org/v2/guide/transitions.html -->
</template>


<script>
export default {
  name: "Modal",
};
</script>


<style lang="scss" scoped>
.modal {
  width: 100%;
  height: 100%;
  z-index: 10;
  display: flex;
  align-items: stretch;
  overflow-x: scroll;
}
.container {
  height: 100%;
  width: 100%;
  display: flex;
}
</style>