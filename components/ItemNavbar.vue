<template>
  <a 
  href="$attrs.href"
  class="text-sm py-0.5 px-4 rounded-full uppercase"
  :class="{
    'bg-acqua text-white font-semibold': active,
    'active': !active
  }">
    <slot></slot>
  </a>
</template>

<style scoped>
.active {
  background-color: white;
  color: #00ccbc;
}
</style>

<script setup>
onMounted(() => {
  const observer = new IntersectionObserver(entries => {
    entries.forEach(entry => {
      console.log(entry);
      // const id = entry.target.getAttribute('id');
      if (entry.intersectionRatio > 0) {
        document.querySelector(`nav li a[href="#${id}"]`).parentElement.classList.add('active');
      } else {
        document.querySelector(`nav li a[href="#${id}"]`).parentElement.classList.remove('active');
      }
    });
  });
})
defineProps({
  active: Boolean
})
</script>
