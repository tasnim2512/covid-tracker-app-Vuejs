<template>
  <div>
    <select @change="Onchange()" v-model="selected" class="w-full mt-10 p-4">
      <option value="0">Select country</option>
      <option v-for="country in countries" :key="country" :value="country.ID">{{ country.Country}}</option>
    </select>
  </div>
</template>
<script>
export default {
  name:'CountrySelect',
  props:['countries'],
  data() {
    return {
      selected:0
    }
  },
  methods:{
    Onchange(){
      const country = this.countries.find((item) => item.ID === this.selected);
      //console.log(country)
      this.$emit('get-country',country)
    }
  }
}
</script>