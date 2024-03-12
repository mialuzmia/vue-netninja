<template>
  <div class="home">
    <h2>My name is {{ name }} and my age is {{ age }}</h2>

    <button @click="handleClick">click me</button>
    <input type="text" v-model="name">

    <button @click="decrease">-</button>
    <button @click="increase">+</button>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  name: 'Home',
  setup() {

    // const title = ref(null)
    
    const name = ref('Mia Luz')
    const age = ref(19)

    const handleClick = () => {
      name.value = 'luisa'
    }

    const increase = () => {
      age.value++
    }
    const decrease = () => {
      age.value--
    }


    return { name, age, handleClick, increase, decrease }
  }
}
</script>
