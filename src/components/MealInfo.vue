<script setup>
defineProps({
  data: {
    type: Object,
    required: true,
  },
});
</script>

<template>
  <section class="meal-info">
    <h1>{{ data.strMeal }}</h1>
    <img :src="data.strMealThumb" :alt="data.strMeal" />
    <div class="short-info">
      <div>
        <h3>Category:</h3>
        <span>{{ data.strCategory }}</span>
      </div>
      <div>
        <h3>Area:</h3>
        <span>{{ data.strArea }}</span>
      </div>
      <div v-if="data.strTags">
        <h3>Tags:</h3>
        <span>{{ data.strTags }}</span>
      </div>
    </div>
    <div>
      <h3>Instructions</h3>
      <p>{{ data.strInstructions }}</p>
    </div>
  </section>
</template>

<style lang="scss" scoped>
.meal-info {
  display: flex;
  flex-direction: column;
  gap: map-get($spacing, "2");

  h1 {
    text-align: center;
    color: map-get($gray, "900");
    font-weight: 800;
  }

  img {
    border-radius: 12px;
  }

  .short-info {
    div {
      display: flex;
      gap: map-get($spacing, "2");
    }
  }

  div {
    h3 {
      font-weight: 500;
    }

    p {
      color: map-get($gray, "500");
      text-align: justify;
    }
  }

  @include phone {
    h1 {
      font-size: 30px;
      line-height: 30px;
    }

    img {
      max-width: 100%;
    }
  }

  @include tablet {
    h1 {
      font-size: 34px;
      line-height: 34px;
    }
  }

  @include desktop {
    h1 {
      font-size: 48px;
      line-height: 48px;
    }

    img {
      max-width: 400px;
    }
  }
}
</style>
