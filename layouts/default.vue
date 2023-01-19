<template>
  <div style="display: flex; height: 100vh; flex-direction: column">
    <HeaderComponent />
    <Nuxt style="flex: 1" />
    <FooterComponent />
  </div>
</template>

<script>
import HeaderComponent from '@/components/HeaderComponent'
import FooterComponent from '@/components/FooterComponent'

export default {
  name: 'Default',
  components: {
    HeaderComponent,
    FooterComponent
  },
  head: {
    title: 'Luatic'
  }
}
</script>

<style scoped>

</style>
