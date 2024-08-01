<script>
export default {
  props: {
    title: {
      type: String,
    },
  },
  data() {
    return {
      currentTime: new Date().toLocaleDateString()
    };
  },
  created() {
    setInterval(() => {
      this.currentTime = new Date().toLocaleDateString();
    }, 1000);
  }
}
</script>

<template>
  <div class="bg-barBottom flex absolute w-full bottom-0 left-0 py-0.5 px-4 text-sm ">
    <div class="w-1/2 text-left">
      {{ currentTime }}
    </div>
    <div class="w-1/2 flex justify-end">
      <slot />
    </div>
  </div>
</template>