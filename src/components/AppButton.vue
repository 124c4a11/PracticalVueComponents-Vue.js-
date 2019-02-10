<template>
  <router-link
    :to="to"
    :disabled="disabled"
    :class="[
      themes[theme],
      sizes[size],
      {
        'disabled': disabled
      }
    ]"
    @click.native="clicked"
    class="btn"
  >
    <slot/>
  </router-link>
</template>

<script>
export default {
  props: {
    theme: {
      type: String,
      default: 'primary'
    },

    size: {
      type: String,
      default: 'normal'
    },

    disabled: {
      type: Boolean,
      default: false
    },

    to: {
      default () {
        return ''
      }
    }
  },

  data () {
    return {
      themes: {
        primary: 'btn-primary',
        danger: 'btn-danger'
      },

      sizes: {
        normal: '',
        large: 'btn-lg'
      }
    }
  },

  methods: {
    clicked (e) {
      if (this.disabled) return

      this.$emit('click', e)
    }
  }
}
</script>
