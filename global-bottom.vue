<template>
  <footer class="absolute bottom-3 right-3" v-if="($slidev.nav.currentPage > 1)">
    {{ ($slidev.nav.currentPage - 1) + '/' + ($slidev.nav.total - 1) }}
  </footer>
</template>