<template>
  <div class="item-inner">
    <span class="index"># {{ index }}</span>
    <input class="checkbox" v-bind:checked="checked" @change="onChange" type="checkbox" />
    <span class="name" @click="onClickName">{{ name }}</span>
  </div>
</template>

<script>
import mixins from '../../mixins'

export default {
  name: 'keep-state-item',

  mixins: [mixins],

  props: {
    id: String,
    index: Number,
    name: String,
    checked: Boolean
  },

  methods: {
    onChange (e) {
      this.dispatch('keep-state', 'checkBoxValueChange', this.id, e.target.checked)
    },

    onClickName () {
      this.dispatch('keep-state', 'checkBoxValueChange', this.id, !this.checked)
    }
  }
}
</script>

<style lang="less" scoped>
.item-inner {
  position: relative;
  display: flex;
  align-items: center;
  .index {
    margin-right: 1em;
  }
  .name {
    margin-left: 1em;
    cursor: pointer;
    user-select: none;
  }
  .checkbox {
    text-align: center;
    width: 30px;
    height: 30px;
    border: none;
    outline: none;
    appearance: none;
    margin: 0;
  }
  .checkbox {
    background-repeat: no-repeat;
    background-position: center left;
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='30' height='30' viewBox='-10 -18 100 135'%3E%3Ccircle cx='50' cy='50' r='50' fill='none' stroke='%23ededed' stroke-width='3'/%3E%3C/svg%3E");
  }
  .checkbox:checked {
    background-image: url("data:image/svg+xml,%3Csvg xmlns='http://www.w3.org/2000/svg' width='30' height='30' viewBox='-10 -18 100 135'%3E%3Ccircle cx='50' cy='50' r='50' fill='none' stroke='%23c28ce2' stroke-width='3'/%3E%3Cpath fill='%239b4dca' d='M72 25L42 71 27 56l-4 4 20 20 34-52z'/%3E%3C/svg%3E");
  }
}
</style>