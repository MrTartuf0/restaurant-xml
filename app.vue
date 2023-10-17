<template>
  <header class="px-16 pb-8 pt-10">
    <div class="image-banner" />
    <section>
      <h1 class="font-bold font-stratos text-[40px]">Rosticceria I Mori</h1>
      <div class="pt-2">Pizza · Italiano</div>
      <div class="pt-2 text-coal-400">Distanza: 1.29 km · Apre alle 12:00 · Minimo d'ordine: 10,00 € · Consegna gratuita</div>
      <div class="pt-4 flex gap-3 cursor-pointer">
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
  <nav class="px-16 py-6 gap-2 uppercase flex border-t border-t-black/10 sticky top-0 bg-white">
    <div class="bg-acqua text-white font-semibold text-sm px-4 py-0.5 rounded-full">arancine</div>
    <div class="bg-white text-acqua font-semibold text-sm px-4 py-0.5 rounded-full">peccati di gola</div>
  </nav>
  <main class="px-16 pt-8 bg-background w-full h-[4000px]">
    Main menù
  </main>
</template>

<style scoped>
  header{
    display: grid;
    gap: 24px;
    grid-template-columns: 30% 1fr;
    grid-template-areas: "image info";
  }
  .image-banner{
    background-image: url('~/assets/img/rosticceria_mori.jpeg');
    border-radius: 4px;
    background-position: center center;
    background-repeat: no-repeat;
    background-size: cover;
    height: 300px;
  }
  nav{
    box-shadow: 0 2px 4px #0000000d;
  }
</style>
