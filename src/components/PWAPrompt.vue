<template>
  <div v-if="shown" class="pwa-prompt">
    <p class="pwa-prompt__text">Add app to home screen?</p>
    <button class="btn btn--main" @click="installPWA">
      Install!
    </button>

    <button class="btn" @click="dismissPrompt">
      No, thanks
    </button>
  </div>
</template>

<script>
export default {
  name: "PWAPrompt",
  data: () => ({
    shown: false,
  }),

  beforeMount() {
    window.addEventListener('beforeinstallprompt', (e) => {
      e.preventDefault()
      this.installEvent = e
      this.shown = true
    })
  },

  methods: {
    dismissPrompt() {
      this.shown = false
    },

    installPWA() {
      this.installEvent.prompt()
      this.installEvent.userChoice.then((choice) => {
        this.dismissPrompt() // Hide the prompt once the user's clicked
        if (choice.outcome === 'accepted') {
          // Do something additional if the user chose to install
        } else {
          // Do something additional if the user declined
        }
      })
    },
  }
}
</script>

<style scoped lang="scss">
  .pwa-prompt {
    background-color: cornflowerblue;
    color: #fff;
    border: 2px solid #fff;
    padding: 1rem;
    max-width: 400px;
    position: absolute;
    top: 2rem;
    right: 2rem;
    &__text {
      margin: 1rem;
    }
  }

</style>
