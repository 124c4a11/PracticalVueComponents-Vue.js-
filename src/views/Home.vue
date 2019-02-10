<template>
  <div>
    <app-label forInput="email">Enter your email address</app-label>
    <app-input type="email" id="email" placeholder="enter email"/>
    <app-textarea v-model="form.bio"/>
  </div>
</template>

<script>
import AppInput from '@/components/AppInput'
import AppLabel from '@/components/AppLabel'
import AppTextarea from '@/components/AppTextarea'

export default {
  name: 'home',

  components: {
    AppInput,
    AppLabel,
    AppTextarea
  },

  data () {
    return {
      form: {
        email: '1@1.mail',
        bio: ''
      }
    }
  }
}
</script>
