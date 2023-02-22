<script setup>
import { ref } from "vue";
import BaseBtn from "@/components/BaseBtn.vue";
import NavItem from "./NavItem.vue";

const navItems = ref([
  {
    label: "All Meals",
    href: "/all",
  },
  {
    label: "Random",
    href: "/",
  },
]);
</script>

<template>
  <header>
    <section>
      <nav>
        <NavItem
          v-for="item in navItems"
          :key="item.label"
          :label="item.label"
          :href="item.href"
        />
      </nav>
      <BaseBtn label="Dark" />
    </section>
  </header>
</template>

<style lang="scss" scoped>
header {
  box-shadow: 0px 4px 6px -1px rgba(0, 0, 0, 0.1),
    0px 2px 4px -2px rgba(0, 0, 0, 0.05);

  section {
    @include container("lg");
    @include phone {
      padding: map-get($spacing, "4") map-get($spacing, "5");
    }

    @include tablet {
      padding: map-get($spacing, "4") map-get($spacing, "6");
    }

    @include desktop {
      padding: map-get($spacing, "4") map-get($spacing, "8");
    }
    display: flex;
    justify-content: space-between;
    align-items: center;

    nav {
      display: flex;
      gap: map-get($spacing, "2");

      li {
        list-style: none;
      }
    }
  }
}
</style>
