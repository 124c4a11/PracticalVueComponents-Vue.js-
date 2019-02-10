<template>
  <textarea
    v-bind="$attrs"
    :name="name"
    :value="value"
    :rows="rows"
    @input="$emit('input', $event.target.value)"
    class="form-control"
  ></textarea>
</template>

<script>
export default {
  props: {
    name: {
      type: String,
      default: ''
    },

    value: {
      type: String,
      default: ''
    }
  },

  computed: {
    rows () {
      return Math.max(5, this.value.split('\n').length)
    }
  }
}
</script>
