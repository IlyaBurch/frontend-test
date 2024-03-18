<template>
    <form @submit.prevent="onSubmit">
      <div class="form-builder" v-for="(field, name) in data" >
        <h3>{{ field.name }}</h3>
        
        <div v-for="item in field.items">
          <form-input 
            v-if="item.name === 'name'" 
            :label="item.label" 
            v-model="formData[name][item.name]"
          />
          <form-select 
            v-if="item.name === 'gender'" 
            :label="item.label" 
            :options="item.additional.options"
            v-model="formData[name][item.name]" 
          />
          <form-radio 
            v-if="item.name === 'age'" 
            :label="item.label" 
            :options="item.additional.options"
            v-model="formData[name][item.name]" 
          />
          <form-password 
            v-if="item.name === 'pass'" 
            :label="item.label" 
            v-model="formData[name][item.name]" 
          />
          <form-repeat-password 
            v-if="item.name === 'repeat-pass'" 
            :label="item.label" 
            v-model="formData[name][item.name]" 
          />
        </div>
      </div>

      <button type="submit">Отправить</button>
      <button type="reset">Стереть</button>
    </form>
</template>

<script>

import dataUsers from "@/json/form-config.json";
import FormItem from "@/components/form-items/FormItem.vue";
import FormInput from "@/components/form-items/FormInput.vue";
import FormSelect from "@/components/form-items/FormSelect.vue";
import FormRadio from "@/components/form-items/FormRadio.vue";
import FormPassword from "@/components/form-items/FormPassword.vue";
import FormRepeatPassword from "@/components/form-items/FormRepeatPassword.vue";

export default {
  name: "FormBuilder",
  data(){
    return {
      data: dataUsers,
      formData: {
      },
      isValid: false,
      pass: '',
    }
  },
  methods: {
    onSubmit() {
      console.log("Form data:", this.formData);
      
    },
    createData(){
      for (let a in this.data){
        this.formData[a] = {
          name: '',
          gender: '',
          age: '',
          pass: '',
        };
      }
    }
  },
  beforeMount(){
    this.createData();
  },
  components: {FormPassword, FormRepeatPassword, FormRadio, FormSelect, FormInput, FormItem}
}
</script>

<style scoped>

</style>
