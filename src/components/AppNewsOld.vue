<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Новости {{ date }}</h2>
      <span>Открыто {{ openRate }} раз | Прочитано {{ readRate }} раз</span>
    </div>
    <div class="card">
      <NewsItem
        v-for="item in news" :key="item.id"
        :title="item.title"
        :id="item.id"
        :is-open="item['isOpen']"
        :was-read="item['wasRead']"
        @rate-click="rateChange"
        @read-click="readChange"
        @unread-click="unreadCange"
      />
    </div>
  </div>
</template>

<script>
import NewsItem from '@/components/NewsItem'

export default {
  data () {
    return {
      date: new Date().toLocaleDateString(),
      news: [
        { id: 1, title: 'Джо победил в США', isOpen: false, wasRead: false },
        { id: 2, title: 'Vue набирает обороты', isOpen: false, wasRead: false }
      ],
      openRate: 0,
      readRate: 0
    }
  },
  provide () {
    return {
      news: this.news
    }
  },
  components: {
    NewsItem
  },
  methods: {
    rateChange (id) {
      this.openRate++
      this.news[id - 1].isOpen = !this.news[id - 1].isOpen
    },
    readChange (id) {
      this.readRate++
      this.news[id - 1].wasRead = true
    },
    unreadCange (id) {
      this.readRate--
      this.news[id - 1].wasRead = false
    }
  }
}
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
