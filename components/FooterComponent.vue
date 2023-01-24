<template>
  <div>
    <ModalComponent
      :title="'Add me on discord!'"
      :is-visible="isDiscordModalVisible"
      @toggleModal="toggleDiscordModal()"
    >
      <template #content>
        <span class="cursor-pointer" title="Click to copy" @click="clickToCopy()">
          {{ copyText }}&nbsp;
          <span class="text-muted">{{ clickTip }}</span>
          <span v-if="!clickTip" style="height: 23px; margin-top: -5px; position: absolute">
            <clipboard-check-icon />
          </span>
        </span>
      </template>
    </ModalComponent>

    <footer>
      <div class="footer-parent container">
        <div>
          <div class="footer-content-block">
            <h6>Contact me</h6>
            <br>
            <a href="mailto:luavanloon@gmail.com">luavanloon@gmail.com</a>
          </div>
          <div class="footer-content-block">
            <a href="https://github.com/luatiq/luatic/" target="_blank">Source code</a>
          </div>
        </div>
        <div>
          <div class="footer-content-block">
            <h6>Socials</h6>
            <ul>
              <li>
                <a href="https://github.com/luatiq/" target="_blank" title="Github">
                  <img src="../assets/images/github-cat.svg" alt="Github">
                </a>
              </li>
              <li>
                <a href="https://tech.lgbt/@luatic" target="_blank" title="Mastodon" rel="me">
                  <img src="../assets/images/mastodon_logo-white.svg" alt="Mastodon">
                </a>
              </li>
              <li>
                <button type="button" class="footer-button" title="Discord" @click="isDiscordModalVisible = true">
                  <img src="../assets/images/discord-mark-white.svg" alt="Discord">
                </button>
              </li>
            </ul>
          </div>
          <div class="footer-content-block sb-0">
            <p>
              <RouterLink :to="`/keyboards/${keeb}`" class="underline">{{ keeb }}</RouterLink>
              Made this page
            </p>
          </div>
        </div>
      </div>
    </footer>
  </div>
</template>

<script>
import { ClipboardCheckIcon } from 'vue-tabler-icons'
import ModalComponent from '@/components/ModalComponent'

export default {
  name: 'FooterComponent',
  components: {
    ModalComponent,
    ClipboardCheckIcon
  },
  data () {
    return {
      keeb: 'Ciel60',
      copyText: 'Lua#6969',
      clickTip: '(click to copy)',
      isDiscordModalVisible: false
    }
  },
  methods: {
    toggleDiscordModal () {
      this.isDiscordModalVisible = !this.isDiscordModalVisible
      this.clickTip = '(click to copy)'
    },
    clickToCopy () {
      this.clickTip = null

      navigator.clipboard.writeText(this.copyText).then(
        () => {
          setTimeout(() => {
            this.toggleDiscordModal()
          }, 800)
        },
        () => {
          this.clickTip = 'Could not copy to clipboard, please do it manually..'
        }
      )
    }
  }
}
</script>

<style scoped>

</style>
