<template>
  <button :class="color" @click="$emit('button-click')">
    <slot></slot>
  </button>
</template>

<script>
export default {
  emits: ['button-click'],
  props: {
    color: {
      type: String,
      default: '',
      validator (value) {
        return ['', 'btn', 'primary', 'danger'].includes(value)
      }
    }
  }
}
</script>

<style>

</style>
