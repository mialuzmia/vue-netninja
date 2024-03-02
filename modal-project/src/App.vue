<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>

  <teleport to='#modals' >
    <Modal theme="sale" v-if="showModal" @close="toggleModal" >
      <h1>Ninja Givaway!</h1>
      <p>Grab your ninja swag for half price!</p>
  
      <template v-slot:links>
        <a href="#">sign up now</a>
        <a href="#">more info</a>
      </template>
    </Modal>
  </teleport>

  <teleport to='#modals'>
    <Modal v-if="showModalTwo" @close="toggleModalTwo">
      <h1>Stormlight Archives</h1>
      <p>Read the series by Brandon Sanderson</p>
    </Modal>
  </teleport>


  <button @click="toggleModal">open modal</button>
  <br>
  <button @click="toggleModalTwo">open modal two</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'My first Vue App :)',
      // header: 'Titúlo Legal',
      // text: 'Conteúdo legal',
      showModal: false,
      showModalTwo: false,
    }
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  }
}
</script>

<style>
#app, #modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}

button{
  margin-bottom: 10px;
  cursor: pointer;
}
</style>
