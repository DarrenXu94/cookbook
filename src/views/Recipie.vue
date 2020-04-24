<template>
  <div class="recipie">
    <div id="recipie__image" class="recipie__image"></div>
    <section class="blank"></section>

    <section class="recipie__info_bar layout">
      <section class="recipie__info_item layout-item-33">
        <div class="recipie__info_item_heading">Time</div>
        <div class="recipie__info_item_value">{{time}} mins</div>
      </section>
      <section class="recipie__info_item layout-item-33">
        <div class="recipie__info_item_heading">Rating</div>
        <div class="recipie__info_item_value">
          <star-rating
            class="center-stars"
            v-model="rating"
            :read-only="true"
            :star-size="20"
            :show-rating="false"
            :border-width="4"
            border-color="#d8d8d8"
            :rounded-corners="true"
            :star-points="[23,2, 14,17, 0,19, 10,34, 7,50, 23,43, 38,50, 36,34, 46,19, 31,17]"
          ></star-rating>
        </div>
      </section>
      <section class="recipie__info_item layout-item-33">
        <div class="recipie__info_item_heading">Cost</div>
        <div class="recipie__info_item_value">${{cost}}</div>
      </section>
    </section>

    <section class="end_blank"></section>

    <section class="recipie__ingredients">
      <header class="recipie__ingredients-header">Ingredients</header>
      <section class="recipie__ingredients_body">
        <div
          class="recipie__ingredients_body-item"
          v-for="(item, index) in ingredients"
          :key="index"
        >{{ item }}</div>
        <!-- <div class="recipie__ingredients_body-item">{{ ingredients }}</div> -->
      </section>
    </section>
    <section class="recipie__directions">
      <header class="recipie__directions-header">Directions</header>
      <section class="recipie__directions">
        <div
          class="recipie__directions-item"
          v-for="(item, index) in directions"
          :key="index"
        >{{ item }}</div>
      </section>
    </section>
  </div>
</template>

<script>
import { fetchById } from "../services/api.service";

export default {
  name: "Recipie",
  async mounted() {
    // console.log(this.$route);
    const res = await fetchById(this.$route.params.id);
    const data = res[0];
    console.log(data);
    this.rating = data.rating;
    this.time = data.time;
    this.cost = data.cost;
    this.ingredients = data.ingredients.split("\n");
    this.directions = data.directions.split("\n");

    const imgHoverDiv = document.getElementById(`recipie__image`);
    const img = "url(" + data.image + ")";
    imgHoverDiv.style.backgroundImage = img;
    imgHoverDiv.style.backgroundPosition = "center";
  },
  data() {
    return {
      ingredients: "",
      directions: "",
      rating: 1,
      time: 0,
      cost: 0
    };
  }
};
</script>

<style lang="scss">
.recipie__image {
  grid-area: recipie_image;
  background-size: cover;
  min-height: 400px;
}
section.blank {
  grid-area: blank_area;
}
section.end_blank {
  grid-area: blank_area_end;
}
section.recipie__info_bar {
  grid-area: info_bar;
  background: white;
}
section.recipie__ingredients {
  grid-area: ingredients;
  background: rgb(236, 235, 235);
}
section.recipie__directions {
  grid-area: directions;
  background: white;
}
.recipie {
  display: grid;
  grid-template-columns: 0.25fr 1fr 2fr 0.25fr;
  grid-template-rows: 3fr 0.5fr 3fr;
  grid-template-areas:
    "blank_area recipie_image   recipie_image blank_area_end"
    "blank_area info_bar        info_bar blank_area_end"
    "blank_area ingredients     directions blank_area_end";
}

.recipie__info_item {
  text-align: center;
  display: flex;
  flex-direction: column;
  justify-content: center;
}

.recipie__info_item_value {
  font-size: 1.1rem;
}

.recipie__ingredients {
  padding: 1rem;
}

.recipie__ingredients-header {
  font-size: 1.7rem;
  color: #ad7d52;
  font-weight: bold;
}

.recipie__ingredients_body {
  margin-top: 1rem;
}

.recipie__ingredients_body-item {
  padding-bottom: 1rem;
}

.recipie__directions {
  padding: 1rem;
}

.recipie__directions-header {
  font-size: 1.7rem;
  color: #ad7d52;
  font-weight: bold;
}

.recipie__directions_body {
  margin-top: 1rem;
}

.recipie__directions-item {
  font-size: 1.2rem;
  padding-bottom: 1rem;
}

@media screen and (max-width: 959px) {
  .recipie {
    grid-template-columns: 1fr 2fr;
    grid-template-rows: 1fr 0.3fr 3fr;
    grid-template-areas:
      "recipie_image recipie_image"
      "info_bar        info_bar"
      "ingredients     directions";
  }
}

@media screen and (max-width: 599px) {
  .recipie {
    // display: flex;
    // flex-direction: column;
    grid-template-columns: 1fr;
    grid-template-rows: 5fr 0.5fr auto auto;
    grid-template-areas:
      "recipie_image"
      "info_bar"
      "ingredients"
      "directions";
  }

  section.recipie__info_bar {
    padding: 5px;
  }
}
</style>