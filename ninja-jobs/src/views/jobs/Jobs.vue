<template>  
  <h1>Jobs</h1>

  <template v-if="jobs.length > 0">
    <div v-for="job in jobs" :key="job.id" class="job">
      <router-link :to="{ name: 'jobDetails', params: { id: job.id } }">
        <h2>{{ job.title }}</h2>
      </router-link>
    </div>
  </template>
  
  <p v-else>Loading jobs...</p>
</template>

<script>
  export default {
    data() {
      return {
        jobs: [],
      }
    },
    methods: {
      async getJobs() {
        try {
          const response = await fetch('http://localhost:3000/jobs')
          this.jobs = await response.json()
          console.log('response: ',response)
        } catch (error) {
          console.log(error.message)
        }
      },
    },
    mounted() {
      this.getJobs()
      console.log('jobs: ', this.jobs)
    },
  }
</script>

<style scoped>

.job h2 {
  background: #f4f4f4;
  padding: 20px;
  border-radius: 10px;
  margin: 10px auto;
  max-width: 600px;
  cursor: pointer;
  color: #444;
}
.job h2:hover {
  background: #ddd; 
}
.job a {
  text-decoration: none;  
}

</style>