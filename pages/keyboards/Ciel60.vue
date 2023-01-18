<script setup></script>

<template>
  <keyboard-slot :keeb="keeb">
    <template #title>
      <h1 class="top-heading">
        The daily driver.
      </h1>
    </template>

    <template #about>
      <section>
        <p>
          I bought the Ciel60 kit because I wanted to try an O-ring mounted keyboard with a weight, I was not prepared
          for just how good it would be.
        </p>

        <h2 class="top-heading">
          Component selection
        </h2>
        <p>
          I did not put much thought into the keyboard kit (case, pcb, plate, o-ring) itself. Though
          obviously I did have some requirements:
        </p>

        <ul>
          <li>
            A cute color. this kit had a
            <span style="background: #FCB0FF; color: black; padding: 0 .25rem">lilac</span>
            option, perfect!
          </li>
          <li>
            A somewhat flexible plate, but not too flexible. By default it came with steel, but I wanted FR4.
            Why settle?
          </li>
          <li>
            A soft mount. This kit always mounts via O-ring, but by default it's a 50A o-ring. How are my poor fingers
            gonna type on that? I needed the softer 30A o-ring.
          </li>
        </ul>

        <h4 class="not-a-heading">
          That's it for the kit, it's Switch&trade; time.
        </h4>
        <p>
          I needed linear switches that were not too light. I also wanted to have a box stem for as little stem wobble
          as possible. Also, I like the sound of a POM stem.
        </p>
        <p>
          While this does not narrow it down as much as I would have liked, it did give me something to work with.
          Luckily these switches are pink! Just my favorite wavelength of light, yay!
        </p>

        <h4 class="not-a-heading">
          Now for the keycaps
        </h4>
        <p>
          I've run with multiple sets for this keeb. And my by-far favourite is a simple black-on-white set, I went with
          MW CMM BOW. How clean!
        </p>

        <h4 class="not-a-heading">
          We do a little bit of foaming
        </h4>
        <p>
          I wanted to go for the popular "marbly" sound, but without muting <b>everything</b>. So I went with foam for
          in between the plate & pcb. The case does also have foam though! Just not an entire mat like most keyboards
          have. I kept it simple with a thin strip of EVA foam.
        </p>
      </section>
    </template>
  </keyboard-slot>
</template>

<!-- <style>
    @import '@/assets/home.css';
</style> -->

<script>
import ciel60 from './specs/ciel60.json'
import KeyboardSlot from '@/slots/KeyboardSlot'

export default {
  components: {
    KeyboardSlot
  },
  data () {
    return {
      keeb: ciel60
    }
  }
}
</script>
