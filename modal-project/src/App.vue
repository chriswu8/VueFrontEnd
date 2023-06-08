<template>
<h1>test</h1>
  <h1>{{ title }} </h1>
  <input type="text" ref="name">
  <button @click="handleClick">Click me</button>
  <Modal header="Sign up for the newsletter!" :text="text" theme="sale" /> <!-- props (to be accepted by Modal child component) -->
  <!-- Props: 1) make components more dynamically reusable by passing different content (from parent) and 
              2) when multiple components use same data, we only have to define those data in ONE place (in parent component)-->
  <!-- <Modal :header="['Chris', 111]" :text="text" theme="sale" />  -->

</template>

<script>

import Modal from './components/Modal.vue'

export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: 'My First Vue App',
      header: 'Sign up for the newsletter!',
      text: '1234567'
    }
  },
  methods: {
    handleClick()
    {
      console.log(this.$refs.name)
      this.$refs.name.classList.add('active') // adds a class to ref="name" tag
      this.$refs.name.focus() // the focus goes to ref="name" tag
    }
  }
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

