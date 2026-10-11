<template>
  <h1>{{ title }}</h1>
  <p>Welcome</p>
  <!-- <input id="input" type="text" ref="name" />
  <button @click="handleClick">Click Me</button> -->
  <teleport to=".modals" v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <template v-slot:links>
        <a href="#"> sign up now</a>
        <a href="#"> more info</a>
      </template>
      <h1>Title</h1>
      <p>Some paragraph</p>
    </Modal>
  </teleport>
  <teleport to=".modals" v-if="showModalTwo">
    <Modal theme="none" @close="toggleModalTwo">
      <template v-slot:buttons>
        <a href="#">Fuk yuu</a>
        <p>or</p>
        <a href="#">Fuk Mee</a>
      </template>
      <h1>Hello</h1>
      <p>You have to choos between Fuk sisters !!!</p>
    </Modal>
  </teleport>
  <button @click.alt="toggleModal">Open Modal (alt)</button>
  <button @click.shift="toggleModalTwo">Open Modal Two (shift)</button>
</template>

<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: "My first vue app :-)",
      showModal: false,
      showModalTwo: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },
};
</script>

<style>
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid#ddd;
  display: inline-block;
  padding-bottom: 10px;
}
.active {
}
</style>
