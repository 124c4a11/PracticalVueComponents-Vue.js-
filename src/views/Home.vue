<template>
  <div>
    <app-button @click.prevent="onClick">Create account</app-button>
  </div>
</template>

<script>
import AppButton from '@/components/AppButton'

export default {
  name: 'home',

  components: {
    AppButton
  },

  methods: {
    onClick () {
      console.log('clicked')
    }
  }
}
</script>
