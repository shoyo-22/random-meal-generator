<script setup>
defineProps({
  label: {
    type: String,
    default: "",
  },
});
</script>

<template>
  <button type="button">
    {{ label }}
  </button>
</template>

<style lang="scss" scoped>
$btn-padding: 10px 20px;
$btn-flex-gap: 8px;
$btn-border-radius: 8px;

button {
  display: inline-flex;
  justify-content: center;
  align-items: center;
  gap: $btn-flex-gap;
  padding: $btn-padding;
  border: 1px solid map-get($primary, "700");
  border-radius: $btn-border-radius;
  background-color: map-get($primary, "700");
  color: $white;
  font-family: inherit;
  font-weight: 500;
  font-size: 14px;
  line-height: 21px;
  transition: all 0.3s ease-in-out;
  cursor: pointer;

  &:hover,
  &:focus {
    background-color: map-get($primary, "800");
  }

  &:focus {
    box-shadow: 0 0 0 3px map-get($primary, "200");
  }
}
</style>
