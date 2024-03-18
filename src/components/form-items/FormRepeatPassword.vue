<template>
  <FormInput :label="label" type="password" required/>
  {{ pass }}
</template>

<script>
import FormInput from "@/components/form-items/FormInput.vue";

export default {
  name: "FormRepeatPassword",
  data(){
    return{
      isValid: false,
    }
  },
  props: {
    label: {
      type: String,
      default: ''
    },
    check:{
      type: Boolean,
      default: false,
    },

  },
  components: {
    FormInput
  }
}
</script>

<style lang="scss" scoped>

</style>