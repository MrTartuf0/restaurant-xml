<template>
  <button 
  class="px-6 py-3 font-bold rounded w-full"
  :class="{
    'bg-coal-200 text-coal-300': variant === 'disabled',
    'bg-acqua text-white': variant === 'primary'
  }">
    <slot></slot>
  </button>
</template>

<script setup>
  defineProps({
    variant: {
      type: String,
      default: 'primary',
      validator: value => ['primary', 'disabled'].includes(value)
    }
  })
</script>
