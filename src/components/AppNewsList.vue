<template>
  <h3>Все новости:</h3>
  <ul v-for="item in news" :key="item.id">
    <li>{{ item.title }}</li>
  </ul>
  <hr />
</template>

<script>
export default {
  inject: ['news']
}
</script>

<style>

</style>
