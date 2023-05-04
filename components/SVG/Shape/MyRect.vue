<script setup>
const props = defineProps({
  x1: {
    type: Number,
    required: true,
  },
  y1: {
    type: Number,
    required: true,
  },
  x2: {
    type: Number,
    required: true,
  },
  y2: {
    type: Number,
    required: true,
  },
})
</script>

<template>
  <path :d="`M ${x1} ${y1} L ${x2} ${y1} L ${x2} ${y2} L ${x1} ${y2} Z`" />
</template>