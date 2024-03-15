<template>
      <p>{{ data.name }}</p>
        <!-- <form @submit.prevent="onSubmit" > -->
          <div v-for="item in data.items">
            <form-input v-if="item.name === 'name'" :label="item.label" v-model="input"/>
            <form-select v-if="item.name === 'gender'" :label="item.label" :options="item.additional.options"/>
            <form-radio v-if="item.name === 'age'" :label="item.label" :options="item.additional.options"/>
            <form-password v-if="item.name === 'pass'" :label="item.label"/>
            <form-password v-if="item.name === 'repeat-pass'" :label="item.label"/>
          </div>
          {{ data }}
        <!-- </form> -->
</template>

<script>
import FormInput from "@/components/form-items/FormInput.vue";
import FormSelect from "@/components/form-items/FormSelect.vue";
import FormRadio from "@/components/form-items/FormRadio.vue";
import FormPassword from "@/components/form-items/FormPassword.vue";
import FormRepeatPassword from "@/components/form-items/FormRepeatPassword.vue";

export default {
  name: "FormItem",

  props: {
    data: {
      type: Object,
        required: true
    },
    keyObj:{
      type: String,
      required: true,
    }
  },
  data() {
    return{
      input: '',
      password: '',
      repeatPassword: '',
      select: '',
      radio: '',
      obj: {
      },
    }
  },
  methods: {
    onSubmit() {
      // Создаем новый JSON с данными формы
      // const formJson = JSON.stringify(this.formData, null, 2);

      // Выводим результат в консоль или отправляем его куда-нибудь
      console.log(this.obj[keyObj]);
    },
  },
  components: {FormPassword, FormRepeatPassword, FormRadio, FormSelect, FormInput}
}
</script>

<style scoped>

</style>