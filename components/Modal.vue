<template>
  <v-dialog
    :value="value"
    :width="width"
    :persistent="persistent"
    @input="$emit('input', arguments[0])"
  >
    <slot />
  </v-dialog>
</template>

<script>
export default {
  props: {
    width: {
      type: String,
      default: '590px'
    },
    value: {
      type: Boolean,
      required: true,
      default: false
    },
    persistent: {
      type: Boolean,
      default: false
    }
  }
}
</script>
