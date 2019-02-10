<template>
  <div>
    <app-button @click.prevent="openModal">Open modal</app-button>
    <app-sign-in-modal/>
  </div>
</template>

<script>
import AppButton from '@/components/AppButton'
import AppSignInModal from '@/components/modals/AppSignInModal'

export default {
  name: 'home',

  components: {
    AppButton,
    AppSignInModal
  },

  methods: {
    openModal () {
      this.$modal.show('signin', { name: 'John' })
    }
  }
}
</script>
