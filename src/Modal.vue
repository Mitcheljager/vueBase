<template>
  <transition
    name="modal"
    enter-active-class="modal--is-entering"
    leave-active-class="modal--is-leaving">
    <div id="modal" class="modal">
      <div class="modal__container">
        <div class="modal__header">
          <slot name="header"></slot>
        </div>
        <div class="modal__content">
          <slot name="body"></slot>
        </div>
        <button class="button modal__action" v-on:click="$emit('closeModal')">Close Modal</button>
      </div>
    </div>
  </transition>
</template>

<script>
export default {
  name: 'modal'
}
</script>

<style lang="scss">
.modal {
  background: rgba(0,0,0,0.5);
  height: 100%;
  width: 100%;
  position: fixed;
  left: 0;
  top: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: opacity 300ms;
  z-index: 100;
}

.modal__container {
  flex: 0 0 auto;
  width: 100%;
  max-width: 640px;
  background: #fff;
  border-radius: 5px;
  padding: 40px;
  transition: transform 300ms;
  display: flex;
  flex-direction: column;
}

.modal__header {
}

.modal__content {
  padding-bottom: 40px;
}

.modal__action {
  margin-top: auto;
}

.modal--is-entering {
  opacity: 0;

  .modal__container {
    transform: translateY(-50px);
  }
}

.modal--is-leaving {
  opacity: 0;

  .modal__container {
    transform: translateY(50px);
  }
}

</style>
