<template>
  <div v-show="isOpen" class="fixed top-0 left-0 w-full h-full flex items-center justify-center">
    <div @click="closeModal()" class="w-screen h-screen fixed bg-black/50 top-0 left-0" />
    <div class="relative max-w-xl bg-background rounded-t overflow-clip">
      <header class="bg-white p-4 flex items-center justify-between font-bold border-b border-b-black/10">
        <div />
        <p>Informazioni</p>
        <img @click="closeModal()" class="w-6 cursor-pointer" src="~/assets/icons/close.svg" alt="close">
      </header>
      <main>
        <h1 class="text-2xl px-4 pt-6 pb-4 font-bold">Informazioni su Rosticceria I Mori</h1>
        <div class="bg-white border-y border-y-black/10 p-4 text-sm">
          Ci siamo impegnati affinché nel nostro piccolo angolo di Sicilia voi possiate vivere un esperienza inedita, di un altro livello... L'amore e la dedizione in ogni nostro singolo piatto, l'attenzione alla cura dei dettagli e un po' di fantasia, questo sono I Mori.
        </div>
        <h1 class="text-2xl px-4 pt-6 pb-4 font-bold">Allergeni</h1>
        <div class="bg-white border-y border-y-black/10 p-4">
          <p class="text-sm">Hai delle domande? Chiedi a Rosticceria I Mori informazioni più dettagliate sui metodi di cottura e sugli ingredienti utilizzati.</p>
          <a href="tel:+393279484011" class="flex gap-2 items-center pt-4 border-t border-t-black/10 mt-4">
            <img class="w-6" src="~/assets/icons/phone.svg" alt="phone">
            <p class="text-acqua">Chiama Rosticceria I Mori al numero +393279484011</p>
          </a>
        </div>
        <h1 class="text-2xl px-4 pt-6 pb-4 font-bold">Indirizzo</h1>
        <div class="bg-white border-y border-y-black/10 p-4">
          <iframe src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2938.8426624216486!2d12.643075312723228!3d42.55863367105506!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x132efb4efa0c32e5%3A0xb0815e760b8eaa66!2sRosticceria%20I%20Mori!5e0!3m2!1sit!2sit!4v1697632905983!5m2!1sit!2sit" width="100%" height="190" style="border:0;" loading="lazy" referrerpolicy="no-referrer-when-downgrade"></iframe>
          <p class="pt-4 text-sm">4 Largo Caduti di Nasiriya, Terni, 05100</p>
          <a href="https://www.google.com/maps/search/?api=1&query=Rosticceria+I+Mori,4+Largo+Caduti+di+Nasiriya%2C+Terni%2C+05100" class="flex gap-2 items-center pt-4 border-t border-t-black/10 mt-4">
            <img class="w-6" src="~/assets/icons/map.svg" alt="phone">
            <p class="text-acqua">Vedi Mappa</p>
          </a>
        </div>
      </main>
    </div>
  </div>
</template>

<script setup>
// Ref variables
const isOpen = ref(false)
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
</script>
