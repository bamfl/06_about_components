<template>
  <div class="container pt-1">
    <div class="card">
      <async-component></async-component>
      <h2>Динамические и асинхронные компоненты</h2>

      <app-button ref="myBtn" :color="oneColor" @button-click="activeOne">
        One
      </app-button>
      <app-button :color="twoColor" @button-click="activeTwo">
        Two
      </app-button>
    </div>

    <!-- <app-text-one v-if="active === 'one'"></app-text-one>
    <app-text-two v-else></app-text-two> -->

    <keep-alive><component :is="componentName"></component></keep-alive>
  </div>
</template>

<script>
import AppButton from '@/components/AppButton'
import AppTextOne from '@/components/AppTextOne'
import AppTextTwo from '@/components/AppTextTwo'

export default {
  data () {
    return {
      active: 'one'
    }
  },
  components: {
    AppButton, AppTextOne, AppTextTwo
  },
  methods: {
    activeOne () {
      this.active = 'one'
    },
    activeTwo () {
      this.active = 'two'
    }
  },
  mounted () {
    // this.componentName = 'new comp name'
    console.log(this.$refs.myBtn)
  },
  computed: {
    componentName: {
      get () {
        return 'app-text-' + this.active
      },
      set (value) {
        console.log(value)
      }
    },
    oneColor () {
      return this.active === 'one' ? 'btn primary' : 'btn'
    },
    twoColor () {
      return this.active === 'two' ? 'btn primary' : 'btn'
    }
  }
}
</script>

<style scoped>

</style>
