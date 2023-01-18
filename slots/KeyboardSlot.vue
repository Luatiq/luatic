<template>
  <div class="container keeb-main">
    <main>
      <slot name="title">
        <h1>
          Keebs
        </h1>
      </slot>

      <slot name="about">
        <section>
          About keeb!
        </section>
      </slot>
    </main>

    <aside class="card keeb-specs-card">
      <table>
        <thead>
          <tr style="display: none">
            <td>&nbsp;</td>
            <td>&nbsp;</td>
          </tr>
        </thead>
        <tbody>
          <tr class="keebSpecsClickable" title="Toggle info" @click="toggleDetails('case', $event)">
            <td>Case</td>
            <td>{{ keeb.case.display }}</td>
            <td :class="detailsVisible.case ? 'caseChevronOpen' : ''">
              <ChevronRightIcon />
            </td>
          </tr>
        </tbody>
        <transition name="accordion">
          <tbody v-if="detailsVisible.case" class="specs-detailed">
            <tr>
              <td>Material</td>
              <td>{{ keeb.case.material }}</td>
            </tr>
            <tr>
              <td>Dampening</td>
              <td>{{ keeb.case.dampening }}</td>
            </tr>
          </tbody>
        </transition>
        <tbody>
          <tr class="keebSpecsClickable" title="Toggle info" @click="toggleDetails('pcb', $event)">
            <td>PCB</td>
            <td>{{ keeb.pcb.display }}</td>
            <td :class="detailsVisible.pcb ? 'pcbChevronOpen' : ''">
              <ChevronRightIcon />
            </td>
          </tr>
        </tbody>
        <transition name="accordion">
          <tbody v-if="detailsVisible.pcb" class="specs-detailed">
            <tr>
              <td>Dampening</td>
              <td>{{ keeb.pcb.dampening ? keeb.pcb.dampening : 'None' }}</td>
            </tr>
            <tr>
              <td>Mounting style</td>
              <td>{{ keeb.pcb.mounting_style }}</td>
            </tr>
            <tr>
              <td>Flex cuts</td>
              <td>{{ keeb.pcb.flex_cuts ? 'Yes' : 'No' }}</td>
            </tr>
            <tr>
              <td>Thickness</td>
              <td>{{ keeb.pcb.thickness + 'mm' }}</td>
            </tr>
          </tbody>
        </transition>
        <tbody>
          <tr class="keebSpecsClickable" title="Toggle info" @click="toggleDetails('plate', $event)">
            <td>Plate</td>
            <td>{{ keeb.plate.material }}</td>
            <td :class="detailsVisible.plate ? 'plateChevronOpen' : ''">
              <ChevronRightIcon />
            </td>
          </tr>
        </tbody>
        <transition name="accordion">
          <tbody v-if="detailsVisible.plate" class="specs-detailed">
            <tr>
              <td>Dampening</td>
              <td>{{ keeb.plate.dampening }}</td>
            </tr>
          </tbody>
        </transition>
        <tbody>
          <tr class="keebSpecsClickable" title="Toggle info" @click="toggleDetails('switches', $event)">
            <td>Switches</td>
            <td>{{ keeb.switches.display }}</td>
            <td :class="detailsVisible.switches ? 'switchesChevronOpen' : ''">
              <ChevronRightIcon />
            </td>
          </tr>
        </tbody>
        <transition name="accordion">
          <tbody v-if="detailsVisible.switches" class="specs-detailed">
            <tr>
              <td>Type</td>
              <td>{{ keeb.switches.type }}</td>
            </tr>
            <tr>
              <td>Top housing material</td>
              <td>{{ keeb.switches.top_housing }}</td>
            </tr>
            <tr>
              <td>Bottom housing material</td>
              <td>{{ keeb.switches.bottom_housing }}</td>
            </tr>
            <tr>
              <td>Stem material</td>
              <td>{{ keeb.switches.stem }}</td>
            </tr>
            <tr>
              <td>Number of pins</td>
              <td>{{ keeb.switches.nr_of_pins }}</td>
            </tr>
            <tr>
              <td>Total travel</td>
              <td>{{ keeb.switches.total_travel + 'mm' }}</td>
            </tr>
            <tr>
              <td>Actuation travel</td>
              <td>{{ keeb.switches.actuation_travel + 'mm' }}</td>
            </tr>
            <tr>
              <td>Actuation force</td>
              <td>{{ keeb.switches.actuation_force + 'g' }}</td>
            </tr>
            <tr>
              <td>Bottom-out force</td>
              <td>{{ keeb.switches.bottom_out_force + 'g' }}</td>
            </tr>
            <tr>
              <td>Lubed with</td>
              <td>{{ keeb.switches.lube }}</td>
            </tr>
          </tbody>
        </transition>
        <tbody>
          <tr class="keebSpecsClickable" title="Toggle info" @click="toggleDetails('keycaps', $event)">
            <td>Keycaps</td>
            <td>{{ keeb.keycaps.display }}</td>
            <td :class="detailsVisible.keycaps ? 'keycapsChevronOpen' : ''">
              <ChevronRightIcon />
            </td>
          </tr>
        </tbody>
        <transition name="accordion">
          <tbody v-if="detailsVisible.keycaps" class="specs-detailed">
            <tr>
              <td>Profile</td>
              <td>{{ keeb.keycaps.profile }}</td>
            </tr>
            <tr>
              <td>Material</td>
              <td>{{ keeb.keycaps.material }}</td>
            </tr>
            <tr>
              <td>Legend method</td>
              <td>{{ keeb.keycaps.legend_method }}</td>
            </tr>
          </tbody>
        </transition>
        <tbody>
          <tr class="keebSpecsClickable" title="Toggle info" @click="toggleDetails('stabs', $event)">
            <td>Stabilizers</td>
            <td>{{ keeb.stabs.display }}</td>
            <td :class="detailsVisible.stabs ? 'stabsChevronOpen' : ''">
              <ChevronRightIcon />
            </td>
          </tr>
        </tbody>
        <transition name="accordion">
          <tbody v-if="detailsVisible.stabs" class="specs-detailed">
            <tr>
              <td>Mounting type</td>
              <td>{{ keeb.stabs.mounting_type }}</td>
            </tr>
            <tr>
              <td>Stem material</td>
              <td>{{ keeb.stabs.stem }}</td>
            </tr>
            <tr>
              <td>Housing material</td>
              <td>{{ keeb.stabs.housing }}</td>
            </tr>
            <tr>
              <td>Lubed with</td>
              <td>{{ keeb.stabs.lube }}</td>
            </tr>
          </tbody>
        </transition>
        <tbody>
          <tr class="keebSpecsClickable" title="Toggle info" @click="toggleDetails('suppLayouts', $event)">
            <td>Supported layouts</td>
            <td>{{ keeb.supported_layouts.length }}</td>
            <td :class="detailsVisible.suppLayouts ? 'suppLayoutsChevronOpen' : ''">
              <ChevronRightIcon />
            </td>
          </tr>
        </tbody>
        <transition name="accordion">
          <tbody v-if="detailsVisible.suppLayouts" class="specs-detailed">
            <tr v-for="(layout) in keeb.supported_layouts" :key="layout">
              <td class="select-none">&nbsp;</td>
              <td>
                {{ layout }}
              </td>
            </tr>
          </tbody>
        </transition>
      </table>
    </aside>
  </div>
</template>

<script>
export default {
  name: 'KeyboardSlot',
  props: {
    keeb: Object
  },
  data () {
    return {
      detailsVisible: {
        case: false,
        pcb: false,
        plate: false,
        switches: false,
        keycaps: false,
        stabs: false,
        suppLayouts: false
      }
    }
  },
  methods: {
    toggleDetails (arg) {
      this.detailsVisible[arg] = !this.detailsVisible[arg]
    }
  }
}
</script>

<style>
@import '@/assets/styles/keyboards.css';
</style>
