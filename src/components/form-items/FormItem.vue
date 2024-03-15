<template>
      <p>{{ data.name }}</p>
        <form @submit.prevent="onSubmit" >
          <!-- <form-input :label="data.items.label"/> -->
          <div v-for="item in data.items">
            <form-input v-if="item.type === 'input'" :label="item.label" v-model="input"/>
            <form-select v-if="item.type === 'select'" :label="item.label" :options="item.additional.options"/>
            <form-radio v-if="item.type === 'radio'" :label="item.label" :options="item.additional.options"/>
            <form-password v-if="item.type === 'password'" :label="item.label"/>
          </div>

          <button type="submit">Отправить</button>
          <button type="reset">Стереть</button>
        </form>
</template>

<script>
import FormInput from "@/components/form-items/FormInput.vue";
import FormSelect from "@/components/form-items/FormSelect.vue";
import FormRadio from "@/components/form-items/FormRadio.vue";
import FormPassword from "@/components/form-items/FormPassword.vue";

export default {
  name: "FormItem",

  props: {
    data: {
      type: Object,
        required: true
    },
  },
  data() {
    return{
      input: '',
      password: '',
      select: '',
      radio: '',
    }
  },
  components: {FormPassword, FormRadio, FormSelect, FormInput}
}
</script>

<style scoped>

</style>