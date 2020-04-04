<template>
  <div>
    <div v-for="item in LandingRecipies" :key="item.id">
      <RecipieCard :recipie="item" />
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
</style>