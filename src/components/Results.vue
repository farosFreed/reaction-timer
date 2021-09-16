<template>
  <p>Reaction Time: {{ score }} ms</p>
  <p>Rank: {{ rank }} </p>
</template>

<script>
export default {
  props: ['score'],
  data() {
      return {
          rank: null
      }
  },
  mounted() {
      if (this.score < 300) {
        this.rank = 'Ninja Fingers'
      } else if (this.score < 450) {
        this.rank = 'Cool'
      } else {
        this.rank = 'Turtle Toes'
      }
  }
}
</script>

<style>

</style>