<template>
  <div v-if="!loading">
    <data-title :text="title" :dataDate="dataDate" />
    <data-boxes :stats="status" />
    <country-select :countries="countries" @get-country="getCountryData" />
      <button
      v-if="status.Country" class="bg-green-700 text-white rounded p-3 mt-10 focus:outline-none hover:bg-green-600"
      @click="clearCountryData">
      Clear Country
    </button>
  </div>
  <div v-else class="flex flex-col justify-center items-center text-center">
    <div class="text-gray-600">Fetching Data</div>
    <img class="w-40 m-auto" :src="loadingImage" alt="" srcset="" />
  </div>
</template>

<script>
// @ is an alias to /src
import DataTitle from "@/components/dataTitle.vue";
import DataBoxes from "@/components/dataBoxes.vue";
import CountrySelect from "@/components/countrySelect.vue";
export default {
  components: {
    DataTitle,
    DataBoxes,
    CountrySelect,
  },
  data() {
    return {
      dataDate: "",
      loading: true,
      status: {},
      countries: [],
      title: "Global",
      loadingImage: require("../assets/dribbble_hourglass.gif"),
    };
  },
  methods: {
    async fetchApiData() {
      const res = await fetch("https://api.covid19api.com/summary");
      const data = await res.json();
      return data;
    },
    getCountryData(country) {
      this.status=country;
      this.title=country.Country;
    },
    async clearCountryData(){
      this.loading=true;
      const data = await this.fetchApiData();
      this.status=data.Global
      console.log(data.Global)
      this.title="Global";
      this.loading=false
    }
  },
  async created() {
    const data = await this.fetchApiData();
    this.dataDate = data.Date;
    this.loading = false;
    this.status = data.Global;
    //console.log(this.status)
    this.countries = data.Countries;
  },
};
</script>
