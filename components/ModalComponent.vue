<template>
  <transition name="modal">
    <div v-if="isVisible" class="modal-backdrop" @click="$emit('toggleModal')">
      <div class="modal" @click.stop>
        <div class="modal-header">
          <h1 class="inline-block modal-title">
            {{ title }}
          </h1>
          <a
            href="#"
            title="Close"
            class="modal-close"
            @click="$emit('toggleModal')"
          ><x-icon /></a>
        </div>

        <div class="modal-content">
          <slot name="content">
            <p>Content here..</p>
          </slot>
        </div>

        <a v-if="button" :href="button.link">
          <button type="button">{{ button.content }}</button>
        </a>
      </div>
    </div>
  </transition>
</template>

<script>
import { XIcon } from 'vue-tabler-icons'

const props = {
  title: String,
  button: false,
  isVisible: false
}

export default {
  name: 'ModalComponent',
  components: {
    XIcon
  },
  props
}
</script>

<style scoped>
  h1 {
    font-size: 20pt;
    margin: 0;
  }
</style>
