<template>
  <div class="loader-wrap">
    <div class="spinner"></div>
  </div>
</template>

<script setup>
</script>

<style scoped>
.loader-wrap {
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 200px;
}

.spinner {
  border: 8px solid var(--gray);
  border-top: 8px solid var(--blue);
  border-radius: 50%;
  width: 60px;
  height: 60px;
  animation: spin 1s linear infinite;
}

@keyframes spin {
  100% {
    transform: rotate(360deg);
  }
}
</style>
