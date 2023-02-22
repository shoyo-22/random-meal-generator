<script setup>
import { onMounted, ref } from "vue";

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
    <button type="button" @click="generateRandMeal">Generate</button>
    <div v-if="loading">Loading...</div>
    <div v-else>
      <div>ID: {{ meal.idMeal }}</div>
      <div>Name: {{ meal.strMeal }}</div>
      <div>Category: {{ meal.strCategory }}</div>
      <div>Country (origin): {{ meal.strArea }}</div>
      <div>
        <h4>Instrcutions</h4>
        <p>{{ meal.strInstructions }}</p>
      </div>
      <div class="image">
        <img :src="meal.strMealThumb" alt="" />
      </div>
      <div>Tags: {{ meal.strTags }}</div>
    </div>
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

  img {
    max-width: 100%;
  }

  transition: all 0.3s ease-in-out;
}
</style>
