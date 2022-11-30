<template>
  <div class="text-center pt-8">
    <h1 class="text-3xl font-bold text-gray-600">{{text}}</h1>
    <h2 class="text-xl font-medium py-3">{{timestamp}}</h2>
  </div>
</template>

<script>
import moment from 'moment'
export default {
  name:'dataTitle',
  props:['text','dataDate'],
  computed:{
    timestamp: function () {
      return moment(this.dataDate).format('LL')
    }
  }
}
</script>