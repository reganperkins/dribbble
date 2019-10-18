<template>
  <transition name="modal">
    <div class="modal">
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
  z-index: 10;
  display: flex;
  align-items: stretch;
  top: 0;
  bottom:0;
  position:fixed;
  overflow-y: scroll;
  overflow-x: hidden;
}
.container {
  width: 100%;
}
</style>