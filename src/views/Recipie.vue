<template>
  <div class="recipie">
    <div class="recipie__image"></div>
    <section class="blank"></section>

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

    <section class="end_blank"></section>

    <section class="recipie__ingredients">
      <header class="recipie__ingredients-header">Ingredients</header>
      <section class="recipie__ingredients_body">
        <div
          class="recipie__ingredients_body-item"
          v-for="(item, index) in RecipiePage"
          :key="index"
        >{{ item }}</div>
      </section>
    </section>
    <section class="recipie__directions">Directions</section>
  </div>
</template>

<script>
import RecipiePage from "../mock/RecipiePage.json";

export default {
  name: "Recipie",
  mounted() {
    this.RecipiePage = this.RecipiePage.split("\n");
  },
  data() {
    return {
      RecipiePage: `4 tablespoons (60g) unsalted butter, cut into 4 pieces and divided
2 celery ribs (5 oz; 140g), peeled (optional) and cut into small dice
2 medium shallots (60g), minced
1/2 cup (30g) finely chopped fresh parsley leaves, divided
4 medium garlic cloves (15g), finely minced
1 fresh green Thai chili (4g), thinly sliced (optional, see note)
Freshly ground black pepper
Two (8-ounce; 237ml) bottles clam juice
Two (6.5-ounce; 184g) cans chopped or minced clams, clams and liquid divided
1 lb (450g) spaghetti
1 teaspoon (5ml) soy sauce
Kosher salt
Celery leaves (pale yellow-green leaves from the celery heart), for garnish
Lemon wedges, for serving`
    };
  }
};
</script>

<style lang="scss">
.recipie__image {
  grid-area: recipie_image;
  background: url("https://images.pexels.com/photos/45202/brownie-dessert-cake-sweet-45202.jpeg?auto=compress&cs=tinysrgb&h=750&w=1260")
    no-repeat center;
  background-size: cover;
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
  background: #202020;
}
.recipie {
  display: grid;
  grid-template-columns: 0.5fr 1fr 2fr 0.5fr;
  grid-template-rows: 3fr 0.5fr 3fr;
  grid-template-areas:
    "recipie_image recipie_image   recipie_image recipie_image"
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
}

.recipie__ingredients_body {
  margin-top: 1rem;
}

.recipie__ingredients_body-item {
  padding-bottom: 1rem;
}

@media screen and (max-width: 959px) {
  .recipie {
    grid-template-columns: 1fr 2fr;
    grid-template-rows: 3fr 0.5fr 3fr;
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
    grid-template-rows: 1fr 0.25fr 1fr 1fr;
    grid-template-areas:
      "recipie_image"
      "info_bar"
      "ingredients"
      "directions";
  }
}
</style>