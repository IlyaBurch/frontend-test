<template>
  <div class="form-builder" v-for="field in data">
    <FormItem :data="field"/>
  </div>
</template>

<script>

import dataUsers from "@/json/form-config.json";
import FormItem from "@/components/form-items/FormItem.vue";

export default {
  name: "FormBuilder",
  data(){
    return {
      data: dataUsers,
    }
  },
  methods: {
    onSubmit() {
      alert('Submit')
    }
  },
  components: {FormItem}
}
</script>

<style scoped>

</style>
