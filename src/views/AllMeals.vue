<script setup>
import { ref } from "vue";

let formData = ref({
  mealName: "",
});
let meals = ref([]);
let loading = ref(false);

async function handleSearch() {
  loading.value = true;
  let query = `https://www.themealdb.com/api/json/v1/1/search.php?s=${formData.value.mealName}`;
  let response = await fetch(query);
  let data = await response.json();
  meals.value = data.meals;
  loading.value = false;
}
</script>

<template>
  <main>
    <section class="form">
      <form @submit.prevent="handleSearch">
        <input
          v-model="formData.mealName"
          type="text"
          placeholder="Enter the name"
        />
        <button type="submit">Search</button>
      </form>
      <button type="button">Filter</button>
    </section>
    <section>
      <div v-if="meals.length">
        <div v-if="loading">Loading...</div>
        <div v-else>
          <article v-for="meal in meals" :key="meal.idMeal">
            {{ meal.strMeal }}
          </article>
        </div>
      </div>
      <div v-else>Search meals on search form</div>
    </section>
  </main>
</template>

<style lang="scss" scoped>
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

  .form {
    display: flex;
    justify-content: space-between;
  }
}
</style>
