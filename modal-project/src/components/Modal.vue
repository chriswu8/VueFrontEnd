// Modal component to be used in App component

<template>
  <div class="backdrop" @click.self="closeModal">                     <!-- listens for click before sending custom event to parent -->
                                                                      <!-- .self applies closeModal method only to the backdrop class & NOT child tags -->
    <div class="modal" :class="{sale_style: theme === 'sale'}">       <!--  custom style based on theme prop value -->
      <!-- h1> {{ header }} </h1> -->     <!-- dynamic prop value -->
      <!-- <p> {{ text }} </p> -->        <!-- dynamic prop value -->

      <slot></slot>
    </div>
  </div>
</template>

<script>
export default {
  // register all props (passed from parent component), must be string
  props: ['header', 'text', 'theme'],
  methods: {
    closeModal() {
      this.$emit('close') // to emit a CUSTOM event called close (to the parent, so that we can set showModal to false)
    }
  }  
};
</script>


<style> /* if scoped, styles only apply to THIS component */
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
  color: #285cd7; /* default <h1> text color */
                    /* can be overridden by sale_style if line 5 check evaluates to true */
}
.modal p {
  font-style: normal; /* will overwrite p style in global.css */
}
.modal.sale_style {
  background: rgb(226, 179, 108);
  color: black;
} 
.modal.sale_style h1 {
  color: white;
}
</style>

