<template>
  <div id="app" class="app">
    <Modal v-if="showModal" v-on:closeModal="showModal = false">
      <h1 slot="header">I am a Modal</h1>
      <p slot="body">
        Hello!
      </p>
    </Modal>

    <Navigation v-if="showNavigation" v-on:closeNavigation="showNavigation = false" v-bind:items="menuItems">

    </Navigation>

    <div class="container">
      <div class="sidebar">
        <a class="sidebar__item" v-on:click="showModal = true">Show Modal</a>
        <a class="sidebar__item" v-on:click="showNavigation = true">Show Menu</a>
      </div>

      <div class="content">
        <Typeahead v-bind:list="countries"></Typeahead>
      </div>
    </div>
  </div>
</template>

<script>
import Modal from './Modal.vue'
import Typeahead from './Typeahead.vue'
import Navigation from './Navigation.vue'

export default {
  name: 'app',
  data () {
    return {
      msg: 'Welcome to Your Vue.js App',
      showModal: false,
      showNavigation: false,
      countries: [
        'Afghanistan', 'Åland Islands', 'Albania', 'Algeria', 'American Samoa', 'AndorrA', 'Angola', 'Anguilla', 'Antarctica', 'Antigua and Barbuda', 'Argentina', 'Armenia', 'Aruba', 'Australia', 'Austria', 'Azerbaijan', 'Bahamas', 'Bahrain', 'Bangladesh', 'Barbados'
      ],
      menuItems: [
        'Home', 'About', 'Shop', 'Contact'
      ]
    }
  },
  components: {
    Modal,
    Typeahead,
    Navigation
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
}

body,
html {
  height: 100%;
  width: 100%;
  margin: 0;
  padding: 0;
}

.app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
  margin: 20px 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #f43059;
  cursor: pointer;
}

.container {
  display: flex;
  flex-direction: row;
  height: 100%;
  width: 100%;
  max-width: 1280px;
  margin: 0 auto;
  padding: 40px 20px;
}

.sidebar {
  flex: 0 0 25%;
  border-right: 1px solid #ddd;
  padding-right: 40px;
}

.sidebar__item {
  display: block;
}

.content {
  flex: 0 0 75%;
  padding-left: 40px;
}

.button {
  border: 0;
  padding: 10px 20px;
  font-size: 16px;
  background: #f43059;
  color: #fff;
  border-radius: 5px;
}

</style>
