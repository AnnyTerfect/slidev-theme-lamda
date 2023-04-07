<script setup>
import { ref, onMounted, nextTick } from 'vue'

const props = defineProps({
  d: {
    type: String,
    required: true,
  }
})

const path = ref(null)
const length = ref(0)

onMounted(() => {
  nextTick(() => {
    length.value = path.value.getTotalLength()
  })
})
</script>

<template>
  <path ref="path" :d="d" class="path" :style="{ '--initial-path-length': length }" />
</template>

<style scoped lang="scss">
.path {
  @apply transition-all;
  stroke-dasharray: var(--initial-path-length);
}

.slidev-vclick-target {
  @apply '!opacity-100';
}

.slidev-vclick-hidden.path {
  stroke-dashoffset: var(--initial-path-length);
}
</style>