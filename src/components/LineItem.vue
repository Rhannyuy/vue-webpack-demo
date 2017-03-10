<template>
  <div class="date-picker">
    Month: <input type="number" ref="monthPicker" :value="parseInt(value.month).toFixed(2)" @input="updateMonth"/>
    Year: <input type="number" ref="yearPicker" :value="parseInt(value.year).toFixed(2)" @input="updateYear"/>
    week: <input type="number" ref="weekPicker" :value="parseInt(value.week).toFixed(2)" @input="updateWeek"/>
    day: <input type="number" ref="dayPicker" :value="parseInt(value.day).toFixed(2)" @input="updateDay"/>
  </div>
</template>

<script>
export default {
  // data () {
  //   return {
  //     value: {
  //       month: 0,
  //       year: 0,
  //       week: 0,
  //       day: 0
  //     }
  //   }
  // },
  props: ['value'],
  methods: {
    updateMonth (evt) {
      this.$emit('changeMonth', parseFloat(evt.target.value))
    },

    updateYear (evt) {
      this.$emit('changeYear', parseFloat(evt.target.value))
      // this.value.year = evt.target.value
      // this.value.month = evt.target.value / 12
      // this.value.week = evt.target.value / 52
      // this.value.day = evt.target.value / 365
    },

    updateWeek (evt) {
      this.$emit('changeWeek', parseFloat(evt.target.value))
      // this.value.week = evt.target.value
      // this.value.day = evt.target.value / 7
      // this.value.month = evt.target.value * 4
      // this.value.year = evt.target.value * 52
    },

    updateDay (evt) {
      this.$emit('changeDay', parseFloat(evt.target.value))
      // this.value.day = evt.target.value
      // this.value.month = evt.target.value * 30
      // this.value.week = evt.target.value * 7
      // this.value.year = evt.target.value * 365
    }
  }
}
</script>
