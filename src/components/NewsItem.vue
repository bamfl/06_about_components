<template>
  <h3>{{ title }}</h3>
  <button class="btn" @click="open">{{ isOpenLocal ? 'Закрыть' : 'Открыть' }}</button>
  <p v-if="isOpenLocal">
    Lorem ipsum dolor, sit amet consectetur adipisicing elit. Incidunt nisi nulla iusto? Ea quia blanditiis amet veritatis, maxime facere voluptatibus quidem illo nam aspernatur, inventore praesentium dolores molestiae, consequatur corporis.
  </p>
</template>

<script>
export default {
  props: {
    title: String,
    id: Number,
    isOpen: Boolean
  },
  data () {
    return {
      isOpenLocal: this.isOpen
    }
  },
  methods: {
    open () {
      this.isOpenLocal = !this.isOpenLocal
      if (this.isOpenLocal) {
        this.$emit('rate-click')
      }
    }
  }
}
</script>

<style>

</style>
