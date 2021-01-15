<template>
  <h3>{{ title }}</h3>
  <app-button color="btn" @button-click="open">{{ isOpen ? 'Закрыть' : 'Открыть' }}</app-button>

  <app-button v-if="wasRead" color="btn danger" @button-click="$emit('unread-click', id)">Отметить непрочитанной</app-button>
  <div v-if="isOpen">
    <hr />
    <p>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Incidunt nisi nulla iusto? Ea quia blanditiis amet veritatis, maxime facere voluptatibus quidem illo nam aspernatur, inventore praesentium dolores molestiae, consequatur corporis.
    </p>
    <app-button v-if="!wasRead" color="btn primary" @button-click="read">Читать новость</app-button>
  </div>
  <hr />
  <app-news-list v-if="isOpen"></app-news-list>
</template>

<script>
import AppButton from '@/components/AppButton'
import AppNewsList from '@/components/AppNewsList'

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
    }
  },
  methods: {
    open () {
      this.$emit('rate-click', this.id)
    },
    read () {
      if (this.isOpen) {
        this.$emit('read-click', this.id)
      }
    }
  },
  components: {
    AppButton, AppNewsList
  }
}
</script>

<style>

</style>
