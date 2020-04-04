<template>
  <div>
    <div class="card_container layout" v-for="item in LandingRecipies" :key="item.id">
      <RecipieCard class="layout-item-50 layout-item-small-100" :recipie="item" />
    </div>
  </div>
</template>

<script>
import LandingRecipies from "../mock/LandingRecipies.json";
// import RecipieCard from "@components/PageLandingComponents/ReceipieCard";
import RecipieCard from "../components/PageLandingComponents/RecipieCard";

export default {
  name: "PageLanding",
  components: {
    RecipieCard
  },
  data() {
    return {
      LandingRecipies: LandingRecipies
    };
  }
};
</script>

<style lang="scss" scoped>
.card_container {
  margin: 0 1rem;
}
</style>