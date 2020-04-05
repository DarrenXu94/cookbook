<template>
  <div class="recipie">
    <div class="recipie__image"></div>

    <section class="recipie__info_bar layout">
      <section class="recipie__info_item layout-item-33">
        <div class="recipie__info_item_heading">Time</div>
        <div class="recipie__info_item_value">15 mins</div>
      </section>
      <section class="recipie__info_item layout-item-33">
        <div class="recipie__info_item_heading">Rating</div>
        <div class="recipie__info_item_value">3</div>
      </section>
      <section class="recipie__info_item layout-item-33">
        <div class="recipie__info_item_heading">Cost</div>
        <div class="recipie__info_item_value">$15.50</div>
      </section>
    </section>
    <section class="recipie__ingredients">Ingredients</section>
    <section class="recipie__directions">Directions</section>
  </div>
</template>

<script>
export default {
  name: "Recipie"
};
</script>

<style lang="scss">
.recipie__image {
  grid-area: recipie_image;
  background: url("https://images.pexels.com/photos/45202/brownie-dessert-cake-sweet-45202.jpeg?auto=compress&cs=tinysrgb&h=750&w=1260")
    no-repeat center;
  background-size: cover;
}
section.recipie__info_bar {
  grid-area: info_bar;
  background: white;
}
section.recipie__ingredients {
  grid-area: ingredients;
  background: #333333;
}
section.recipie__directions {
  grid-area: directions;
  background: #202020;
}
.recipie {
  display: grid;
  grid-template-columns: 1fr 2fr;
  grid-template-rows: 3fr 0.5fr 3fr;
  grid-template-areas:
    "recipie_image   recipie_image"
    "info_bar        info_bar"
    "ingredients     directions"
    "ingredients     directions";
  height: 100%;
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

@media screen and (max-width: 599px) {
  .recipie {
    // display: flex;
    // flex-direction: column;
    grid-template-columns: 1fr;
    grid-template-rows: 1fr 0.25fr 1fr 1fr;
    grid-template-areas:
      "recipie_image"
      "info_bar"
      "ingredients"
      "directions";
  }
}
</style>