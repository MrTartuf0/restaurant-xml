<template>
  <div v-show="isOpen" class="fixed top-0 left-0 w-full h-full flex items-center justify-center">
    <div @click="closeModal()" class="w-screen h-screen fixed bg-black/50 top-0 left-0" />
    <div class="relative max-w-xl bg-white rounded overflow-clip">
      <div class="cursor-pointer absolute top-2 right-4 bg-white p-2 rounded-full shadow">
        <img @click="closeModal()" class="w-6 " src="~/assets/icons/close.svg" alt="close">
      </div>
      <div class="h-[315px] placeholder">
        <img class="w-full h-full object-cover" src="~/assets/img/abburro.jpeg" alt="food">
      </div>
      <main class="pt-4 px-4 pb-6">
        <h1 class="font-stratos text-3xl">ABBURRO</h1>        
        <p class="pt-2">
          RISO ZAFFERANO, BESCIAMELLA, PROSCIUTTO COTTO E MORTADELLA
        </p>
      </main>
      <section class="p-6">
        <div class="flex pb-6 items-center justify-center gap-16">
          <img @click="(counter>1) ? counter-- : null" class="w-6 cursor-pointer" src="~/assets/icons/minus.svg" alt="minus">
          <p class="font-bold text-2xl">
            {{ counter }}
          </p>
          <img @click="counter++" class="w-6 cursor-pointer" src="~/assets/icons/plus.svg" alt="plus">
        </div>
        <AppButton>Aggiungi per 3,20 €</AppButton>
      </section>
    </div>
  </div>
</template>

<style scoped>
.placeholder {
  background-image: url('~/assets/icons/placeholder.svg');
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
}

section {
  -webkit-box-shadow: 0 -1px 4px 0 rgba(0, 0, 0, .08);
  box-shadow: 0 -1px 4px 0 rgba(0, 0, 0, .08);
}
</style>

<script setup>
// Ref variables
const isOpen = ref(true)
const counter = ref(1)
// Functions
function closeModal() {
  isOpen.value = false
}
function openModal() {
  isOpen.value = true
}
// Expose
defineExpose({
  openModal,
  closeModal
})
// Props
defineProps({
  data: {
    type: Object,
    required: true,
  }
})
</script>
