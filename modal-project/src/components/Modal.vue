// Modal component to be used in App component

<template>
  <div class="backdrop">
    <div class="modal" :class="{sale: theme === 'sale'}">
      <h1>{{ header }}</h1>
      <p>Some interesting message</p>
    </div>
  </div>
</template>

<script>
export default {
  // register all props here
  props: ['header', 'text', 'theme']  
};
</script>


<style>
.modal {
  width: 500px;
  padding: 20px;
  margin: 200px auto;
  background: white;
  border-radius: 10px;
}
.backdrop {
  top: 0;
  position: fixed;
  background: rgba(0, 0, 0, 0.5); /* 0.5 makes it semi-transparent */
  width: 100%;
  height: 100%;
}
.modal h1 {
  color: #285cd7;
}
.modal p {
  font-style: normal; /* will overwrite p style in global.css */
}
.modal.sale {
  background: rgb(226, 179, 108);
  color: black;
} 
.modal.sale h1 {
  color: white;
}
</style>

