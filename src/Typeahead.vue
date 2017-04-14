<template>
  <form class="autocomplete">
    <input class="autocomplete__input" type="text" v-on:input="change" v-on:keydown.tab="tab" v-model="value" />

    <span class="autocomplete__result">{{ match }}</span>
  </form>
</template>

<script>
export default {
  name: 'typeahead',
  props: ['list'],
  data() {
    return {
      match: '',
      value: ''
    }
  },
  computed: {
  },
  methods: {
    change: function() {
      var self = this;

      for(var i = 0; i < self.list.length; i++) {
        if (self.list[i].startsWith(self.value)) {
          this.match = self.list[i];
          break;
        } else {
          this.match = '';
        }
      }

      if (self.value == '') {
        this.match = '';
      }
    },
    tab: function() {
      e.preventDefault();
    }
  }
}
</script>

<style lang="scss">
  .autocomplete {
    position: relative;
    line-height: 20px;
    font-size: 21px;
    font-weight: 300;
    font-family: 'Arial';
  }

  .autocomplete__input {
    width: 100%;
    padding: 20px 20px;
    font-size: 21px;
    font-weight: 300;
    font-family: 'Arial';

    &:focus {
      outline: 0;
      border-color: #222;
    }
  }

  .autocomplete__result {
    position: absolute;
    top: 24px;
    left: 22px;
    opacity: 0.3;
  }
</style>
