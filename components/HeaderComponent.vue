<template>
  <header class="container flex">
    <BreadCrumbsComponent />
  </header>
</template>

<script>
import BreadCrumbsComponent from '@/components/BreadCrumbsComponent'

export default {
  name: 'HeaderComponent',
  components: {
    BreadCrumbsComponent
  }
}
</script>

<style scoped>

</style>
