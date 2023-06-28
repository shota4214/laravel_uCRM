<script setup>
import axios from 'axios';
import { ref, onMounted, reactive } from 'vue'

const search = ref('')
const customers = reactive({})

onMounted(() => {
  axios.get('/api/user')
  .then( res => {
    console.log(res.data)
  })
})

const isShow = ref(false)
const toggleStatus = () => { isShow.value = !isShow.value }

const searchCustomers = async () => {
  try {
  await axios.get(`/api/searchCustomers/?search=${search.value}`)
  .then( res => {
    console.log(res.data)
    customers.value = res.data
  })
  toggleStatus()
  } catch(e){
    console.log(e)
  }
}

</script>

<template>
    <div v-show="isShow" class="modal" id="modal-1" aria-hidden="true">
    <div class="modal__overlay" tabindex="-1" data-micromodal-close>
      <div class="modal__container" role="dialog" aria-modal="true" aria-labelledby="modal-1-title">
        <header class="modal__header">
          <h2 class="modal__title" id="modal-1-title">
            Micromodal
          </h2>
          <button @click="toggleStatus" type="button" class="modal__close" aria-label="Close modal" data-micromodal-close></button>
        </header>
        <main class="modal__content" id="modal-1-content">
          <p>
            Try hitting the <code>tab</code> key and notice how the focus stays within the modal itself. Also, <code>esc</code> to close modal.
          </p>
        </main>
        <footer class="modal__footer">
          <button @click="toggleStatus" type="button" class="modal__btn modal__btn-primary">Continue</button>
          <button @click="toggleStatus" type="button" class="modal__btn" data-micromodal-close aria-label="Close this dialog window">Close</button>
        </footer>
      </div>
    </div>
  </div>
  <input name="customer" v-model="search">
  <button @click="searchCustomers" type="button" data-micromodal-trigger="modal-1">検索する</button>
</template>