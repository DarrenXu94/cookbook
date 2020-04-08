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
    <section class="recipie__directions">
      <header class="recipie__directions-header">Directions</header>
      <section class="recipie__directions">
        <div
          class="recipie__directions-item"
          v-for="(item, index) in Directions"
          :key="index"
        >{{ item }}</div>
      </section>
    </section>
  </div>
</template>

<script>
import RecipiePage from "../mock/RecipiePage.json";

export default {
  name: "Recipie",
  mounted() {
    this.RecipiePage = this.RecipiePage.split("\n");
    this.Directions = this.Directions.split("\n");
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
Lemon wedges, for serving`,
      Directions: `1. In a 12-inch stainless steel skillet, melt 2 tablespoons of butter over medium heat, and swirl pan until foaming subsides. Add celery, shallots, half the parsley (1/4 cup; 15g), garlic, Thai chili (if using), and a couple healthy grinds of black pepper to pan and cook, stirring occasionally, until vegetables are soft and mixture is fragrant, 1 to 2 minutes. Add bottled clam juice along with liquid from canned clams but not the clam meat. Increase heat to high and bring mixture to a boil, then reduce heat to a simmer until liquid is slightly reduced and vegetables have infused broth, about 5 minutes—there should be enough liquid in the pan to fully submerge the pound of cooked pasta. Turn off heat and add clam meat and soy sauce.

2. In a pot of salted, boiling water, cook spaghetti, stirring frequently, until about 4 minutes shy of the way you like your pasta cooked (some would say "al dente"). When spaghetti is almost at that point of doneness, bring pan of clam sauce to a boil over high heat.

3. Using tongs, transfer spaghetti to pan with clam sauce, distributing pasta so it is mostly submerged in sauce. Cook, tossing and stirring occasionally, until pasta is cooked to your liking and sauce has thickened slightly, about 4 minutes. Taste for seasoning, and add salt if necessary.

4. Turn off heat, add remaining butter and parsley, and toss and stir spaghetti vigorously to incorporate parsley and emulsify butter into sauce. Divide pasta among four serving plates, spooning sauce and clams evenly over each portion. Garnish with celery leaves, and serve immediately, passing lemon wedges, for squeezing, at the table.`
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