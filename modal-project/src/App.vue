<!-- Autoformat: Shift + Option + F --> 

<template>
  <h1>{{ title }}</h1>
  <p>Welcome!</p>
  <input type="text" ref="name" />
  <br><br>
  <button @click="handleClick">Focus on input field</button>
  <br><br>
  <teleport to=".modals" v-if="showModal">
    <!-- <Modal header="Hardcoded Prop Value" :text="text" theme="sale" @close="toggleModal" /> --> <!-- @close is a custom event -->
    <!-- props (to be accepted by Modal child component) -->
    <!-- Props: 1) make components more dynamically reusable by passing different content (from parent) and 
                2) when multiple components use same data, we only have to define those data in ONE place (in parent component)-->
  
  
    <Modal theme="sale" @close="toggleModal"> <!-- This is a slot used to pass templates (not data)-->
                                              <!-- Notice no closing forward slash / -->

      <template v-slot:links>      <!-- slot direct used to give this template a slot NAME -->
                                   <!-- calling this template "links" -->
        <a href="#">Anchor 1</a>
        &nbsp;
        <a href="#">Anchor 2</a>
      </template>
      <h1> Header within the slot </h1>
      <p> Paragraph within the slot </p>
    </Modal>

  </teleport>

    <teleport to="#modals" v-if="showModal2">
    <Modal theme="chris" @close="toggleModal2"> <!-- This is a slot used to pass templates (not data)-->
                                               <!-- Notice no closing forward slash / -->

      <template v-slot:links2>      <!-- slot direct used to give this template a slot NAME -->
                                    <!-- calling this template "links" -->
        <a href="#">Anchor 1</a>
        &nbsp;
        <a href="#">Anchor 2</a>
        &nbsp;
        <a href="#">Anchor 3</a>
        &nbsp;
        <a href="#">Anchor 4</a>
      </template>
      <h1> Chris Wu's Header </h1>
      <p> Chris Wu's Paragraph </p>
    </Modal>

  </teleport>
  <button @click.shift="toggleModal">Toggle Modal (shift)</button> <!-- .shift event modifier: must press shift first (then click) -->
  &nbsp;
  <button @click.alt="toggleModal2">Toggle Modal (alt)</button>
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
      showModal2: false,
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
    ,
    toggleModal2() {
      this.showModal2 = !this.showModal2;
    }
  },
};
</script>

<style>
#app, .modals, #modals { /** not scoped, so can style .modals and #modals, which are outside of App.vue */
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

