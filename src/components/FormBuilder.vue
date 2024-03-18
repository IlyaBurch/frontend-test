<template>
    <div class="wrapper">
      <form @submit.prevent="onSubmit" class="form form__paddings">
        <div class="form--item" v-for="(field, name) in data">
          <h3 class="item--name">{{ field.name }}</h3>
          <div v-for="item in field.items" class="item--body">
            <form-input
              class="input item--text-input"
              v-if="item.name === 'name'"
              :label="item.label"
              v-model="formData[name][item.name]"
            />
            <form-select
              class="input item--select"
              v-if="item.name === 'gender'"
              :label="item.label"
              :options="item.additional.options"
              v-model="formData[name][item.name]"
            />
            <form-radio
              class="input item--radio"
              v-if="item.name === 'age'"
              :label="item.label"
              :name="name"
              :options="item.additional.options"
              v-model="formData[name][item.name]"
            />
            <form-password
              class="input item--password"
              v-if="item.name === 'pass'"
              :label="item.label"
              v-model="formData[name][item.name]"
            />
            <form-repeat-password
              class="input item--password"
              v-if="item.name === 'repeat-pass'"
              :label="item.label"
              v-model="check[name][item.name]"
              :pattern="formData[name][item.additional.parent]"
            />
          </div>
        </div>
        <div class="form--submit-buttons">
          <button class="button submit-button" type="submit">Отправить</button>
          <button class="button submit-button" type="reset">Стереть</button>
        </div>
      </form>
    </div>
</template>

<script>

import dataUsers from "@/json/form-config.json";
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
      formData: {},
      check:{},
    }
  },
  methods: {
    onSubmit() {
      fetch('https://httpbin.org/post', {
          method: 'POST', 
          body: JSON.stringify(this.formData)
        })
      .then ((response) => response.json())
      .then ((data) => {
        alert(data.data)
      })
    },
    createData(){
      for (let a in this.data){
        this.formData[a] = {
          name: '',
          pass: '',
        };
        this.check[a] = {}
      }
    },
  },
  beforeMount(){
    this.createData();
  },
  components: {FormPassword, FormRepeatPassword, FormRadio, FormSelect, FormInput,}
}
</script>

<style scoped>
.button{
  border: none;
  background: none;
}

.wrapper{
  background-color: #333333;
  display: grid;
  place-items: center;
  color: #333333;
}

.form{
  width: 300px;
  background-color: #fcfaf9;
  border-radius: 15px;
  padding: 20px;
  box-shadow: 0 0 50px  black;
}

.form--submit-buttons{
  display: flex;
  justify-content: space-between;
}
.submit-button{
  background: #48E5C2;
  color: #FCFAF9;
  width: 120px;
  height: 50px;
  border-radius: 16px;
}

.form__paddings{
  margin: 50px 0 50px 0;
}
.input{
  padding: 5px;
}
.item--name{
  padding: 20px;
}
</style>
