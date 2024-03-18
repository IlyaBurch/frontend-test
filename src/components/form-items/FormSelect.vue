<template>
  <div>
    <p>{{ label }}</p>
    <select>
      <option
        v-for="option in options"
        :key="option.value"
        :value="option.value"
        :selected="option.selected"
        @click="$emit('update:modelValue', $event.target.value)"
      >{{ option.text }}
    </option>
    </select>
  </div>
</template>

<script>
export default {
  name: "FormSelect",
  
  props: {
    label: {
      type: String,
      default: ''
    },
    options: {
      type: Object,
      required: true
    }
  },
}
</script>

<style scoped>

</style>
