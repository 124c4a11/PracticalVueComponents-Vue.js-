<template>
  <input
    v-bind="$attrs"
    :type="type"
    :name="name"
    :value="value"
    @input="$emit('input', $event.target.value)"
    class="form-control"
  >
</template>

<script>
export default {
  props: {
    type: {
      type: String,
      default: 'text'
    },

    name: {
      type: String,
      default: ''
    },

    value: {
      type: String,
      default: ''
    }
  }
}
</script>
