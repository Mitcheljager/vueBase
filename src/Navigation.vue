<template>
  <transition
    name="navigation"
    enter-class="navigation--is-entering"
    leave-active-class="navigation--is-leaving">

    <nav class="navigation">
      <a v-for="item in items">{{ item }}</a>
      <button class="navigation__close" v-on:click="$emit('closeNavigation')">Close Menu</button>
    </nav>
  </transition>
</template>

<script>
export default {
  name: 'navigation',
  props: ['items']
}
</script>

<style lang="scss">
  .navigation {
    background: #fff;
    height: 100vh;
    width: 30vw;
    display: flex;
    flex-direction: column;
    position: fixed;
    z-index: 20;
    left: 0;
    top: 0;
    padding: 40px;
    box-shadow: 0 0 15px rgba(0,0,0,0.15);
    transition: transform 500ms;
  }

  .navigation__close {
    margin-top: auto;
    height: 60px;
    background: #fff;
    border: 2px solid #f1f1f1;
    font-size: 16px;
    color: #e1e1e1;
    cursor: pointer;

    &:hover {
      border-color: #aaa;
      color: #777;
    }
  }

  .navigation--is-entering {
    transform: translateX(-100%);
  }

  .navigation--is-leaving {
    transform: translateX(-100%);
  }
</style>
