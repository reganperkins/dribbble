<template>
  <transition name="modal" appear>
    <div class="modal-wrapper">
      <div class="modal-container">
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
</template>

<script>
export default {
  name: "Modal"
};
</script>

<style lang="scss" scoped>
.modal-wrapper {
  width: 100%;
  z-index: 10;
  display: flex;
  align-items: stretch;
  top: 0;
  bottom: 0;
  position: fixed;
  overflow-y: scroll;
  overflow-x: hidden;
  transition: opacity 0.4s ease;
}
.modal-container {
  width: 100%;
  transition: transform 0.2s ease;
}

.modal-enter {
  opacity: 0;
}

.modal-leave-active {
  opacity: 0;
}

.modal-enter .modal-container,
.modal-leave-active .modal-container {
  transform: scale(0.95);
}
</style>
