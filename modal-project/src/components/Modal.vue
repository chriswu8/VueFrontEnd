// Modal component to be used in App component

<template>
  <div class="backdrop" @click.self="closeModal">
    <!-- listens for click before sending custom event to parent -->
    <!-- .self applies closeModal method only to the backdrop class & NOT child tags -->
    <div class="modal" :class="{ sale_style: theme === 'sale', chris_style: theme === 'chris'}">

      <!--  custom style based on theme prop value -->
      <!-- h1> {{ header }} </h1> -->
      <!-- dynamic prop value -->
      <!-- <p> {{ text }} </p> -->
      <!-- dynamic prop value -->

      <!-- populated w/ template pass from parent's <Modal>...</Modal> -->
      <slot>Default Slot Content</slot>
      
      <div class="actions">
        <!-- named slot -->
        <slot name="links"></slot>
        <slot name="links2"></slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  // register all props (passed from parent component), must be string
  props: ["header", "text", "theme"],
  methods: {
    closeModal() {
      this.$emit("close"); // to emit a CUSTOM event called close (to the parent, so that we can set showModal to false)
    },
  },
};
</script>


<style>
/* if scoped, styles only apply to THIS component */
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
  color: #8fa1c9; /* default <h1> text color */
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
/* =================================================== */
.modal.chris_style .actions {            /* style if theme is chris_style */
  text-align: center;
  margin: 30px 0 10px 0;
  color: #333;
}
.modal.chris_style .actions a {          /* style if theme is chris_style */
  color: #333;
  padding: 8px;
  border: 1px solid #eee;
  border-radius: 4px;
  text-decoration: none;
  margin: 10px;
}

.modal.sale_style .actions {
  color: white;
}
.modal.sale_style .actions a {
  color: white;
}
</style>

