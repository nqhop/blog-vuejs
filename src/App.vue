<script lang="ts" setup>
import { computed, ref } from "vue";
import Navbar from "./components/Navbar.vue"
import { useModal } from './composables/modal.js'
import FormInput from "./components/FormInput.vue";

const modal = useModal();

const modalStyle = computed(() => {
  return {
    display: modal.show.value ? 'block' : 'none'
  }
})

const username = ref('')
</script>

<template>
  <div class="modal" style="display: block; color: white;" :style="modalStyle">
    <div class="modal-background">
      <div class="modal-content">
        <div id="modal"></div>
      </div>
    </div>
    <button class="modal-close is-large" @click="modal.hideModal()"></button>
  </div>

  <div class="section">
    <div class="container">
      <FormInput name="Username" v-model="username"/>
      <Navbar />
      <router-view />
      {{ username }}
    </div>
  </div>
</template>

<style>
@import "https://cdn.jsdelivr.net/npm/bulma@0.9.4/css/bulma.min.css";
@import "highlight.js/styles/atom-one-dark.css";

/* over write bulma */
.column {
  text-align: left;
}

ul {
  list-style: revert !important;
  list-style-position: inside !important;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  font-size: revert !important;
  margin: 10px 0 !important;
}

pre {
  margin: 10px 0 !important;
}

p {
  margin: 10px 0 !important;
}
</style>
