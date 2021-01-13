<template>
  <h3>{{ title }}</h3>
  <button class="btn" @click="open">{{ isOpenLocal ? 'Закрыть' : 'Открыть' }}</button>
  <button v-if="wasRead" class="btn danger" @click="$emit('unread-click', id)">Отметить непрочитанной</button>
  <div v-if="isOpenLocal">
    <hr />
    <p>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Incidunt nisi nulla iusto? Ea quia blanditiis amet veritatis, maxime facere voluptatibus quidem illo nam aspernatur, inventore praesentium dolores molestiae, consequatur corporis.
    </p>
    <button v-if="!wasRead" class="btn primary" @click="read">Читать новость</button>
  </div>
</template>

<script>
export default {
  props: {
    title: String,
    id: Number,
    isOpen: Boolean,
    wasRead: Boolean
  },
  emits: {
    'rate-click': null,
    'unread-click': null,
    'read-click' (id) {
      if (id) {
        return true
      } else {
        console.warn('Нет id для emit read-click')
        return false
      }
    }
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
    },
    read () {
      if (this.isOpenLocal) {
        this.$emit('read-click', this.id)
        this.isOpenLocal = !this.isOpenLocal
      }
    }
  }
}
</script>

<style>

</style>
