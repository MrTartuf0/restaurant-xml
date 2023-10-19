<template>
  <div class="rounded cursor-pointer shadow hover:shadow-xl bg-white transition-shadow p-4 flex justify-between space-x-4"
    :class="{
      'border-l-4 border-l-acqua': isPicked
    }"
  >
    <aside class="space-y-1">
      <h1 class="font-bold">
        <span v-show="isPicked" class="text-acqua">{{ counter }}x </span>
        {{ data?.name }}
      </h1>
      <p class="text-coal-400 text-sm max-h-9 text-ellipsis overflow-hidden whitespace-pre-line">
        {{ data?.description }}
      </p>
      <p class="text-coal-400">
        {{ data?.price }}
      </p>
    </aside>
    <div v-if="data?.image" class="rounded border border-black/5 w-24 h-24 overflow-clip shrink-0">
      <img :src="data?.image" alt="food" class="w-full h-full object-cover">
      {{ data?.image }}
    </div>
  </div>
</template>


<script setup>
const isPicked = ref(false)
const counter = ref(1)

// Props
defineProps({
  data: {
    type: Object,
    required: true,
  }
})
</script>
