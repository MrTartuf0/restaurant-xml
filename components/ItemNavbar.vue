<template>
  <a 
  class="text-sm py-0.5 px-4 rounded-full uppercase"
  :class="{
    'bg-acqua text-white font-semibold': active,
    'bg-white text-acqua': !active
  }">
    <slot></slot>
    {{ $attrs.href }}
  </a>
</template>

<script setup>
  defineProps({
    active: Boolean
  })
</script>
