<template>
  <div class="modals">
    <h1>Modals</h1>
    <button @click="showModal = true">Show modal</button>
  </div>
  <Modal v-model="showModal" @hideModal="showModal = false" title="My title (via props)">
    <p>
      Lorem ipsum dolor sit, amet consectetur adipisicing elit. Facilis repellendus repudiandae
      asperiores molestiae quibusdam quas ipsam ab soluta sed eum, doloribus distinctio nihil,
      fugiat dolor. Recusandae autem quo nemo itaque.
    </p>
  </Modal>
</template>

<script setup>
import Modal from '@/components/Modal.vue'
import { ref } from 'vue'

const showModal = ref(false)
</script>
