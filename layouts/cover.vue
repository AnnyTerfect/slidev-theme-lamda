<script setup lang="ts">
import { handleBackground } from '../layoutHelper'
import { computed } from 'vue'

const props = defineProps({
  background: {
    default: '',
  },
})

const style = computed(() => handleBackground(props.background, true))
</script>

<template>
  <div class="slidev-layout cover" :style="style">
    <img class="fixed left-6 top-6 w-25" src="../public/images/nju.png" />
    <img class="fixed w-1/1 left-0 -bottom-3" src="../public/images/nju-bottom.png" />
    <div class="my-auto w-full">
      <slot />
    </div>
  </div>
</template>
