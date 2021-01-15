<template>
  <div class="card">
    <ul>
      <li v-for="item in 5" :key="item">
        <slot :iter="item"></slot>
      </li>
    </ul>
  </div>
</template>

<script>
export default {

}
</script>

<style>

</style>
