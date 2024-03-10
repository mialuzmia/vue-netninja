<template>
  <div v-if="job">
    <h1>{{ job.title }}</h1>
    <p>the job id is: {{ id }}</p>
    <p>{{ job.details }}</p>
  </div>
</template>

<script>
  export default {
    props: ['id'],
    data() {
      return {
        // id: this.$route.params.id,
        job: null, 
      }
    },
    methods: {
      async getJob() {
        try {
          const response = await fetch(`http://localhost:3000/jobs/${this.id}`)
          const data = await response.json()
          this.job = data
          // console.log(data)
        } catch (error) {
          console.log(error.message)
        }
      },
    },
    mounted() {
      this.getJob()
    },
  }
</script>

<style scoped>

</style>