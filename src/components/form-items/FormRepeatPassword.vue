<template>
  <FormInput :label="label" type="password" required :pattern />
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
    pattern:{
      type: String,
      required: true,
    }

  },
  components: {
    FormInput
  }
}
</script>

<style lang="scss" scoped>

</style>