<template>
  <div class="modal">
    <div class="overlay" @click="emit('closeModal')"></div>
    <div class="modal-card">
      <slot />
    </div>
  </div>
</template>

<script>
import { onBeforeUnmount } from 'vue'
export default {
  setup(props, { emit }) {
    let onkeydown = event => {
      console.log(event.key)
      if (event.key === 'Escape') {
        emit('closeModal')
      }
    }
    window.addEventListener('keydown', onkeydown)
    onBeforeUnmount(() => {
      window.removeEventListener('keydown', onkeydown)
    })
    return {
      emit
    }
  }
}
</script>

<style scoped></style>
