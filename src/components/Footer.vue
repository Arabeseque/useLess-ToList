<script setup lang="ts">
const today = ref(new Date())
</script>

<template>
  <nav text-base mt-6 inline-flex gap-2>
    &copy; {{ today.getFullYear() }} The tool for study. All rights reserved.
    <button icon-btn @click="toggleDark()">
      <div dark:i-carbon-moon i-carbon-sun />
    </button>
  </nav>
</template>
