<template>
  <h1>{{ title }}</h1>
  <p>welcome...</p>
  <teleport to="#modals" v-if="showModal">
    <!-- @close is the custom event -->
    <Modal theme="" @close="toggleModal">
      <!-- Slots -->
        <template v-slot:links>
          <a href="#">sign up now</a>
          <a href="#">more info</a>
        </template>
        <h1>Ninja Giveaway!</h1>
        <p>Grab your ninja swag for half price!</p>
    </Modal>
  </teleport>

  <teleport to="#modals" v-if="showModalTwo">
    <Modal @close="toggleModalTwo">
      <template v-slot:linkTwo>
        <a href="#">Button 1</a>
        <a href="#">Button 2</a>
      </template>
      <h1>Sign up to the newsletter</h1>
      <p>For updates and promo codes!</p>
    </Modal>
  </teleport>

  <button @click="toggleModal">open modal (alt)</button>
  <button @click="toggleModalTwo">open modal</button>
  <!-- Template Refs allows us to store a reference to a DOM element inside a variable -->
  <!-- <input type="text" ref="name"> 
  <button @click="handleClick">click me</button> -->
</template>

<script>
import Modal from './components/Modal.vue';

export default {
  name: 'App',
  components: { Modal },
  data() {
    return {
      title: 'My First Vue App :)',
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
</style>
