<template>
  <div
    :style="{'height': `${height}px`}"
    :class="{'selected': selected, 'null-option': nullOption}"
    class="select-item"
    @click="$emit('click')"
  >
    {{ getOptionLabel(option) }}
  </div>
</template>
<script>
export default {
  props: {
    option: {
      type: null,
      required: true,
    },
    selected: {
      type: Boolean,
      required: true,
    },
    height: {
      type: Number,
      default: 48,
    },
    getOptionLabel: {
      type: Function,
      default: value => value,
    },
  },

  computed: {
    nullOption() {
      return this.option === null;
    },
  },
};
</script>
<style lang="scss" scoped>
.select-item {
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  padding: 0 8px;

  transition: background-color 0.5s ease;
  &:hover:not(.selected) {
    background-color: #f8f8f8;
  }

  &.selected {
    background-color: #efefef;
  }
  &.null-option {
    color: #888;
  }

}
</style>
