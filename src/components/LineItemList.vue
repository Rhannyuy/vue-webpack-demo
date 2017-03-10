<template>
    <div>
    <p>LineItemList</p>
    <line-item
      v-for="(item, index) in items"
      v-bind:value="item"
      v-on:changeMonth="updateMonth(index, $event)"
      v-on:changeYear="updateYear(index, $event)"
      v-on:changeWeek="updateWeek(index, $event)"
      v-on:changeDay="updateDay(index, $event)"
    ></line-item>
    <line-total v-bind:items="items"></line-total>
    <button v-on:click="addItem">+</button>
    </div>
</template>

<script>
import LineItem from './LineItem'
import LineTotal from './LineTotal'
export default {
  data () {
    return {
      items: []
    }
  },

  components: {
    'line-item': LineItem,
    'line-total': LineTotal
  },
  methods: {
    addItem () {
      this.items.push({
        month: 0,
        year: 0,
        week: 0,
        day: 0
      })
    },
    updateMonth (index, $event) {
      this.$set(this.items, index, {
        month: $event,
        year: $event * 12,
        week: $event / 4,
        day: $event / 30
      })
    },

    updateYear (index, $event) {
      this.$set(this.items, index, {
        year: $event,
        month: $event / 12,
        week: $event / 52,
        day: $event / 365
      })
    },

    updateWeek (index, $event) {
      this.$set(this.items, index, {
        week: $event,
        month: $event * 4,
        year: $event * 52,
        day: $event / 7
      })
    },

    updateDay (index, $event) {
      this.$set(this.items, index, {
        day: $event,
        month: $event * 30,
        week: $event * 7,
        year: $event * 365
      })
    }
  }
}
   </script>

   <style>

   </style>
