<script setup>
import { ref, onMounted, onBeforeUnmount, computed } from 'vue'
import chongqing from '../components/g6.vue'
const props = defineProps({
  image: {
    type: String,
    required: true,
  },
  imageOrder: {
    type: Number,
    required: true
  }
})


const imageOrderClass = computed(() => {
  return props.imageOrder === 1 ? 'order-1' : 'order-2'
})

onMounted(() => {
  window.addEventListener('resize', () => {
    
  })

})

onBeforeUnmount(() => {

})
</script>

<template>
  <Transition name="slide-fade">
  <div class="slidev-layout grid image-x">
    <div class="my-auto flex">
      <div class="w-1/2 flex justify-center items-center p-8 max-h-md object-cover" :class="imageOrderClass">
        <chongqing ref="myComponent" class="rounded-2xl border-image object-cover"/>
      </div>
      <div class="w-1/2 flex flex-col justify-center" :class="textAlignment">
        <slot />
      </div>
    </div>
  </div>
</Transition>
</template>
<style scoped>
.slide-fade-enter-active {
  transition: all 2s ease-out;
}

.slide-fade-leave-active {
  transition: all 0.8s cubic-bezier(1, 0.5, 0.8, 1);
}

.slide-fade-enter-from,
.slide-fade-leave-to {
  transform: translateX(30px);
  opacity: 0;
}
</style>