<template>
  <div class="slidev-layout two-cols">
    <slot name="default"></slot>
    <div class="grid grid-cols-2 gap-16">
      <div>
        <slot name="left" />
      </div>
      <div>
        <slot name="right"></slot>
      </div>
    </div>
  </div>
</template>
