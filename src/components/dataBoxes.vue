<template>
  <div class="grid md:grid-cols-2 gap-4" >
    <div class="shadow-md bg-blue-100 p-10 text-center rounded-md">
      <h1 class="text-2xl text-blue-800 font-bold">Cases</h1>
      <h1 class="text-xl py-1">
        <span class="font-bold">New: </span>
        {{numberWithCommas(stats.NewConfirmed)}}
      </h1>
        <h1 class="text-xl py-1">
        <span class="font-bold">Total: </span>
        {{numberWithCommas(stats.TotalConfirmed)}}
      </h1>
    </div>
     <div class="shadow-md bg-blue-100 p-10 text-center rounded-md">
      <h1 class="text-2xl text-blue-800 font-bold">Deaths</h1>
      <h1 class="text-xl py-1">
        <span class="font-bold">New: </span>
        {{numberWithCommas(stats.NewDeaths)}}
      </h1>
        <h1 class="text-xl py-1">
        <span class="font-bold">Total: </span>
        {{numberWithCommas(stats.TotalDeaths)}}
      </h1>
    </div>
  </div>
</template>

<script>
export default {
  name:'dataBoxes',
  props:['stats'],
  methods:{
    numberWithCommas(x) {
    return x.toString().replace(/\B(?=(\d{3})+(?!\d))/g, ",");
  }
  },
}
</script>