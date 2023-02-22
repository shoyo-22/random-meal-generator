<script setup>
import { onMounted, ref } from "vue";
import BaseBtn from "@/components/BaseBtn.vue";
import MealInfo from "@/components/MealInfo.vue";

let meal = ref({});
let loading = ref(true);

async function generateRandMeal() {
  loading.value = true;
  let response = await fetch(
    "https://www.themealdb.com/api/json/v1/1/random.php"
  );
  let data = await response.json();
  meal.value = data.meals[0];
  loading.value = false;
}

onMounted(() => {
  generateRandMeal();
});
</script>

<template>
  <main>
    <section class="action">
      <BaseBtn label="Generate" @click="generateRandMeal" />
    </section>
    <div v-if="loading">Loading...</div>
    <MealInfo :data="meal" v-else />
  </main>
</template>

<style scoped lang="scss">
main {
  @include container("lg");
  @include phone {
    padding: map-get($spacing, "5");
  }

  @include tablet {
    padding: map-get($spacing, "6");
  }

  @include desktop {
    padding: map-get($spacing, "8");
  }
  transition: all 0.3s ease-in-out;

  display: flex;
  flex-direction: column;
  gap: map-get($spacing, "4");

  .action {
    display: flex;
    justify-content: center;
  }
}
</style>
