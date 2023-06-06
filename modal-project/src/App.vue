<template>
  <h1>{{ title }}</h1>
  <input type="text" ref="name">
  <button @click="handleClick">Click me</button>
  <aaaaa header="Sign up for the newsletter!" :text="text" theme="sale" /> <!-- header attribute is the prop (to be accepted by Modal) -->
  <!-- <aaaaa :header="['Chris', 111]" :text="text" theme="sale" />  -->

</template>

<script>

import aaaaa from './components/Modal.vue'

export default {
  name: "App",
  components: {
    aaaaa,
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
