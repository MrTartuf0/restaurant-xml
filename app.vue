<template>
  <header class="px-16 pb-8 pt-10">
    <div class="image-banner" />
    <section>
      <h1 class="font-bold font-stratos text-[40px]">Rosticceria I Mori</h1>
      <div class="pt-2">Pizza · Italiano</div>
      <div class="pt-2 text-coal-400">Distanza: 1.29 km · Apre alle 12:00 · Minimo d'ordine: 10,00 € · Consegna gratuita</div>
      <div @click="$refs.infoModal.openModal()" class="pt-4 flex gap-3 cursor-pointer">
        <img class="w-6" src="~/assets/icons/info.svg" alt="info">
        <div class="leading-5">
          <p>Informazioni</p>
          <p class="text-sm">Allergeni e tanto altro</p>
        </div>
        <img class="w-4" src="~/assets/icons/arrow.svg" alt="arrow">
      </div>
      <div class="pt-4 flex gap-3 cursor-pointer">
        <img class="w-6" src="~/assets/icons/star.svg" alt="star">
        <div class="leading-5">
          <p class="text-green">4.6 Eccellente</p>
          <p class="text-sm">Vedi 467 recensioni</p>
        </div>
        <img class="w-4" src="~/assets/icons/arrow.svg" alt="arrow">
      </div>
    </section>
  </header>

  <nav class="px-16 py-6 gap-2 flex border-t border-t-black/10 sticky top-0 bg-white">
    <ItemNavbar active href="arancine">arancine</ItemNavbar>
    <ItemNavbar>peccati di gola</ItemNavbar>
    <ItemNavbar>fish burger</ItemNavbar>
    <ItemNavbar>pizze e calzoni</ItemNavbar>
    <ItemNavbar>dolci</ItemNavbar>
    <ItemNavbar>bevande e lattine</ItemNavbar>
    <ItemNavbar>vini bianchi in bottiglia</ItemNavbar>
  </nav>
  <main class="px-16 pt-8 bg-background w-full h-[4000px]">
    <section>
      <div @click="$refs.infoModal.openModal()" class="border border-coal-100 py-4 pl-4 pr-6 rounded bg-white flex gap-4 items-center cursor-pointer">
        <div>
          <h3 class="pb-1 font-bold">Informazioni su Rosticceria I Mori</h3>
          <p class="text-sm">Ci siamo impegnati affinché nel nostro piccolo angolo di Sicilia voi possiate vivere un esperienza inedita, di un altro livello... L'amore e la dedizione in ogni nostro singolo piatto, l'attenzione alla cura dei dettagli e un po' di fantasia, questo sono I Mori.</p>
        </div>
        <div>
          <div class="w-10 h-10 rounded-full overflow-clip">
            <img class="h-full w-full object-cover" src="~/assets/img/rosticceria_mori.jpeg" alt="pfp">
          </div>
        </div>
      </div>
    </section>
    <aside>
      <div class="bg-white px-4 pb-4 border border-coal-100">
        <div class="flex flex-col gap-1 items-center pt-8">
          <img class="w-12" src="~/assets/icons/basket.svg" alt="basket">
          <p class="text-coal-300">Il carrello è vuoto</p>
        </div>
        <AppButton class="mt-10" variant="disabled">Vai al pagamento</AppButton>
      </div>
    </aside>
  </main>

  <AppModal ref="infoModal"/>

</template>

<script setup>
</script>

<style scoped>
header {
  display: grid;
  gap: 24px;
  grid-template-columns: 30% 1fr;
  grid-template-areas: "image info";
}

.image-banner {
  background-image: url('~/assets/img/rosticceria_mori.jpeg');
  border-radius: 4px;
  background-position: center center;
  background-repeat: no-repeat;
  background-size: cover;
  height: 300px;
}

nav {
  box-shadow: 0 2px 4px #0000000d;
}

main {
  display: grid;
  gap: 24px;
  grid-template-columns: 7fr 3fr;
  grid-template-areas: "menu basket";
}
</style>
