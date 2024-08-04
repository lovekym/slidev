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
</template>