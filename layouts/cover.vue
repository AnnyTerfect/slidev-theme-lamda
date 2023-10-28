<script setup lang="ts">
import { handleBackground } from '../layoutHelper'
import { computed } from 'vue'

const props = defineProps<{
  background: string
  topLeftImg: string
  bottomImg: string
}>()

const style = computed(() => handleBackground(props.background, true))
</script>

<template>
  <div class="slidev-layout cover" :style="style">
    <img v-if="topLeftImg" class="fixed left-6 top-6 w-24" :src="topLeftImg" />
    <img v-if="bottomImg" class="fixed w-1/1 left-0 -bottom-3" :src="bottomImg" />
    <div class="my-auto w-full">
      <slot />
    </div>
  </div>
</template>
