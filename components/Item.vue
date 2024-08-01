<script>
export default {
  props: {
    text: {
      type: String,
      required: true,
      default: '@username'
    },
  }
}
</script>

<template>
  <div class="flex flex-nowrap justify-center items-center ml-4">
    <span class="flex justify-center item-center">
      <slot />
    </span>
    <span class="ml-0.5  animate-marquee">
      {{text}}
    </span>
  </div>
</template>
<style scoped>
@keyframes marquee {
  0% { transform: translateX(0); }
  50% { transform: translateX(-800px); }
  100% { transform: translateX(0); }
}

.animate-marquee {
  display: inline-block;
  animation: marquee 5s linear infinite;
}
</style>