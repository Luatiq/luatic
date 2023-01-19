<template>
  <header class="container flex">
    <h1>Luatic</h1><span style="padding-left: 1rem;" class="subtext">&lsqb;loo‐ah‐tik&rsqb;</span>
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
