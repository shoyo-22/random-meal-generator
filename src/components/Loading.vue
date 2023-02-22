<!-- eslint-disable vue/multi-word-component-names -->
<script setup></script>

<template>
  <div class="overlay">
    <div class="spinner"></div>
  </div>
</template>

<style lang="scss" scoped>
.overlay {
  display: grid;
  place-items: center;

  .spinner {
    width: 40px;
    height: 40px;
    border-radius: 50%;
    display: inline-block;
    border-top: 3px solid map-get($primary, "600");
    box-sizing: border-box;
    animation: rotation 1s linear infinite;
  }
}

@keyframes rotation {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}
</style>
