<template>
  <header class="px-16 pb-8 pt-10">
    <div class="image-banner" :style="`background-image: url('${data?.bannerImg}')`" />
    <section>
      <h1 class="font-bold font-stratos text-[40px]">{{ data?.name }}</h1>
      <div class="pt-2">{{ data?.type }}</div>
      <div class="pt-2 text-coal-400">Distanza: {{ data?.distance }} · Apre alle {{ data?.openingHour }} · Minimo d'ordine: {{ data?.minimumOrder }} · Consegna gratuita</div>
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
          <p class="text-green">{{ data?.rating}}</p>
          <p class="text-sm">Vedi {{ data?.ratingNumber }} recensioni</p>
        </div>
        <img class="w-4" src="~/assets/icons/arrow.svg" alt="arrow">
      </div>
    </section>
  </header>

  <nav class="px-16 py-6 gap-2 flex border-t border-t-black/10 sticky top-0 bg-white">
    <ItemNavbar v-for="item in data?.menu.category">
      {{ item.name }}
    </ItemNavbar>
  </nav>
  <main class="px-16 pt-8 pb-32 bg-background w-full">
    <section>
      <div @click="$refs.infoModal.openModal()" class="border border-coal-100 py-4 pl-4 pr-6 rounded bg-white flex gap-4 items-center cursor-pointer">
        <div>
          <h3 class="pb-1 font-bold">Informazioni su {{ data?.name }}</h3>
          <p class="text-sm">
            {{ data?.description }}
          </p>
        </div>
        <div>
          <div class="w-11 h-11 rounded-full overflow-clip">
            <img class="h-full w-full object-cover" src="~/assets/img/rosticceria_mori.jpeg" alt="pfp">
          </div>
        </div>
      </div>
      <div v-for="item in data?.menu.category">
        <h1 class="pt-8 pb-4 text-[22px] font-bold">
          {{ item.name }}
        </h1>
        <div class="grid grid-cols-3 gap-4">
          <div v-for="product in item.product">
            <h2>{{ product.name }}</h2>
            <p>{{ product.description }}</p>
            <p>{{ product.price }}</p>
          </div>
          <!-- <p>{{ data?.menu.category[0].product[0]?.outOfStock }}</p> -->
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

  <AppModal ref="infoModal" :data="data"/>

</template>

<script>
let data = ref()
</script>
<script setup>
import XMLHttpRequest from 'xhr2'

var xhttp = new XMLHttpRequest();
onMounted(() => {
  xhttp.onreadystatechange = function () {
    if (this.readyState == 4 && this.status == 200) {
      data.value = xml2json(this.responseXML).restaurant
      console.log(xml2json(this.responseXML).restaurant);
      // console.log(this.responseXML.getElementsByTagName("restaurant")[0]);
      // data= this.responseXML
    }
  };
  xhttp.open("GET", "_nuxt/data.xml", true);
  xhttp.send();
})

function xml2json(srcDOM) {
  let children = [...srcDOM.children];
  if (!children.length) {
    return srcDOM.innerHTML
  }
  let jsonResult = {};
  for (let child of children) {
    let childIsArray = children.filter(eachChild => eachChild.nodeName === child.nodeName).length > 1;
    if (childIsArray) {
      if (jsonResult[child.nodeName] === undefined) {
        jsonResult[child.nodeName] = [xml2json(child)];
      } else {
        jsonResult[child.nodeName].push(xml2json(child));
      }
    } else {
      jsonResult[child.nodeName] = xml2json(child);
    }
  }
  return jsonResult;
}

</script>

<style scoped>
header {
  display: grid;
  gap: 24px;
  grid-template-columns: 30% 1fr;
  grid-template-areas: "image info";
}

.image-banner {
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
