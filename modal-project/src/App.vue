<!-- Autoformat: Shift + Option + F --> 

<template>
  <h1>{{ title }}</h1>
  <p>Welcome!</p>
  <input type="text" ref="name" />
  <br><br>
  <button @click="handleClick">Focus on input field</button>
  <br><br>
  <div v-if="showModal">
    <Modal header="Hardcoded Prop Value" :text="text" theme="sale" @close="toggleModal" /> <!-- close is a custom event -->
    <!-- props (to be accepted by Modal child component) -->
    <!-- Props: 1) make components more dynamically reusable by passing different content (from parent) and 
                2) when multiple components use same data, we only have to define those data in ONE place (in parent component)-->
  </div>
  <button @click.shift="toggleModal">Toggle Modal (shift)</button> <!-- .shift event modifier: must press shift first (then click) -->
</template>

<script>
// Import child components before use
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title:     "My First Vue App",
      header:    "Some Amazing Header That Sells",
      text:      "Really persuasive text written by AI",
      showModal: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active");  // adds a class to ref="name" tag
      this.$refs.name.focus();                  // the focus goes to ref="name" tag
    },
    toggleModal() {
      this.showModal = !this.showModal;
    }
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

