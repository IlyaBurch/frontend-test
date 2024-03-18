<template>
  <fieldset>
    <legend>{{ label }}</legend>

    <div
        v-for="option in options"
        :key="option.value"
    >
      <input 
        required 
        type="radio" name="radio" 
        :id="option.value" 
        :value="option.value" 
        :checked="option.selected" 
        @change="$emit('update:modelValue', $event.target.value)"/>
      <label :for="option.value">{{ option.text }}</label>
    </div>
  </fieldset>
</template>

<script>
export default {
  name: "FormRadio",
  data(){
    return{
      // value = this.option.value
    }
  },
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
