<template>
  <div>
    <p>{{ label }}</p>
    <input
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
        :type="type"
        required
    />
  </div>
</template>

<script>
export default {
  name: "FormInput",

  props: {
    label: {
      type: String,
      default: ''
    },
    type: {
      type: String,
      default: 'text'
    },
    modelValue :{
      type: String,
      default: '',
    }
  },
}
</script>

<style scoped>

</style>
