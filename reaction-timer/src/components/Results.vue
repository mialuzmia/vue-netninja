<template>
  <div class="results">
    <p >Reaction time: {{ score }} ms</p>
    <p class="rank">{{ rank }}</p>
  </div>
</template>

<script>
  export default {
    name: 'Results',
    props: {
      score: {
        type: Number,
      },
    },
    data() {
      return {
        rank: '',
      }
    },
    mounted() {
      if (this.score < 250) {
      this.rank = 'Ninja Fingers'
        
      } 
      else if(this.score < 400) {
        this.rank = 'Rapid Reflexes'
      }      
      else {
        this.rank = 'Snail pace...'
      }
    },

  }
</script>

<style scoped>
  .rank{
    font-size: 1.4em;
    color: #0faf87;
    font-weight: bold;
  }
</style>