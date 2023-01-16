<template>
  <main class="container">
    <h1 class="top-heading">
      Keebs
    </h1>
    <section class="card-wrapper">
      <div v-for="keeb in getKeeb()" :key="keeb.display" class="card card-half">
        <h3 style="padding-bottom: 1rem">
          {{ keeb.display }}
        </h3>

        <div>
          <small>Specifications:</small>

          <table class="specs-table">
            <thead>
              <tr>
                <th style="width: 33%" />
                <th />
              </tr>
            </thead>
            <tbody>
              <tr>
                <td>Case:</td>
                <td>{{ keeb.case.display }}</td>
              </tr>
              <tr>
                <td>Switches:</td>
                <td>{{ keeb.switches.display }}</td>
              </tr>
              <tr>
                <td>Keycaps:</td>
                <td>{{ keeb.keycaps.display }}</td>
              </tr>
              <tr>
                <td>Plate:</td>
                <td>{{ keeb.plate.material }}</td>
              </tr>
              <tr>
                <td>Mounting type:</td>
                <td>{{ keeb.pcb.mounting_style }}</td>
              </tr>
            </tbody>
          </table>
        </div>

        <nuxt-link v-if="keeb.display === 'Ciel60'" :to="`/keyboards/${keeb.display}`">
          <button title="Read more..">
            Read more
          </button>
        </nuxt-link>

        <button v-else
                disabled
                title="This page is not yet ready"
        >
          More detailed page coming soon..
        </button>
      </div>
    </section>
  </main>
</template>

<script>
import ciel60 from './specs/ciel60.json'
import ikki68 from './specs/ikki68.json'

export default {
  name: 'AllKeyboardsView',
  data () {
    return {
      keyboards: {
        ciel60,
        ikki68
      }
    }
  },
  methods: {
    getKeeb (display) {
      if (display) {
        return this.keyboards[`${display}`]
      }

      return this.keyboards
    }
  }
}
</script>

<style scoped>

</style>
