<template>
   <table>
     <tr>
       <td>{{getValueTotal() }}</td>
       <td>{{getValueTotal() / 12 }}</td>
       <td>{{getValueTotal() / 52 }}</td>
       <td>{{getValueTotal() / 365 }}</td>
    </tr>
  </table>
</template>

<script>
   export default {
     props: ['items'],
     methods: {
       getValueTotal () {
         var sum = 0
         for (var i = 0; i < this.items.length; i++) {
           sum += this.items[i].year
         }
         return sum
       }
     }
   }
</script>

<style>
  table {
    width: 100%;
    margin: 0;
  }
</style>
