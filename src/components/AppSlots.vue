<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Slots</h2>
    </div>
    <app-list>
      <template #default="{iter}">
        <span style="color: #c25285;">
          {{ iter }}
        </span>
      </template>
    </app-list>
    <app-block>
      <p>Text for slot</p>

      <template #footer>
        <h3>footer</h3>
      </template>

      <template #header>
        <h3>header</h3>
      </template>
    </app-block>
  </div>
</template>

<script>
import AppBlock from '@/components/AppBlock'
import AppList from '@/components/AppList'

export default {
  components: {
    AppBlock, AppList
  }
}
</script>

<style scoped>

</style>
