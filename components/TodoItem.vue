<template lang="html">
  <li @click="handleClicked"> Please say {{ item.text }}
  </li>
</template>

<script>
export default {
   props: ['item'],
   mounted() {

   },
   methods: {
    handleClicked() {
      console.log(JSON.stringify(this.item))
    }
   }
}
</script>

<style lang="css" scoped>

</style>
