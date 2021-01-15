<template>
  <div class="container pt-1">
    <div class="card">
      <h2>Динамические и асинхронные компоненты</h2>

      <app-button color='btn' @button-click="active === 'one'">
        One
      </app-button>
      <app-button color="btn" @button-click="active === 'two'">
        Two
      </app-button>
    </div>
  </div>
</template>

<script>
import AppButton from '@/components/AppButton'

export default {
  data () {
    return {
      active: 'one'
    }
  },
  components: {
    AppButton
  }
}
</script>

<style scoped>

</style>
