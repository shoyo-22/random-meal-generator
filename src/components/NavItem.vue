<script setup>
defineProps({
  label: {
    type: String,
    default: "",
  },
});
</script>

<template>
  <li class="nav-item">
    {{ label }}
  </li>
</template>

<style lang="scss" scoped>
.nav-item {
  padding: map-get($spacing, "3") map-get($spacing, "4");
  border-radius: 6px;
  background-color: $white;
  color: map-get($gray, "500");
  font-weight: 500;
  font-size: 14px;
  line-height: 21px;
  transition: all 0.3s ease-in-out;
  cursor: pointer;

  &:hover,
  &.active {
    background-color: map-get($primary, "600");
    color: $white;
  }
}
</style>
