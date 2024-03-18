<template>
  <div class="input-wrapper">
    <p class="input--label">{{ label }}</p>
    <input class="input--text"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
        :type="type"
        required
        :pattern
    />
    <span class="input--validity"></span>
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
    },
    pattern:{
      type: String
    }
  },
}
</script>

<style scoped>
  input:invalid{
    border: 2px solid red;
  }
  input:invalid + .input--validity::before {
  content: 'Некорректные данные';
  color: red;
}
  .input--text{
  border: 2px solid #F3D3BD;
  border-radius: 8px;
  height: 35px;
}
</style>