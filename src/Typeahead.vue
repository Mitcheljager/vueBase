<template>
  <form class="typeahead">
    <input class="typeahead__input" type="text" v-on:input="change" v-on:keydown.tab="tab" v-model="value" placeholder="Autocomplete... (tab)" />

    <span class="typeahead__result">{{ match }}</span>
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
    tab: function(e) {
      e.preventDefault();

      var self = this;

      if (self.match) {
        this.value = self.match;
      }
    }
  }
}
</script>

<style lang="scss">
  .typeahead {
    position: relative;
    line-height: 20px;
    font-size: 21px;
    font-weight: 300;
    font-family: 'Helvetica';
  }

  .typeahead__input {
    width: 100%;
    padding: 20px 20px;
    font-size: 21px;
    font-weight: 300;
    font-family: 'Helvetica';
    background: transparent;
    border: 1px solid #ddd;

    &:focus {
      outline: 0;
      border-color: #222;

      & + .typeahead__result {
        display: block;
      }
    }

    &::placeholder {
      font-style: italic;
      color: #e1e1e1;
      font-weight: 300;
    }
  }

  .typeahead__result {
    display: none;
    position: absolute;
    top: 23px;
    left: 21px;
    color: #e1e1e1;
    z-index: -1;
  }
</style>
