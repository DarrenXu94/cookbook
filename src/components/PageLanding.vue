<template>
  <div class="page_landing">
    <div class="card_container layout" v-for="item in LandingRecipies" :key="item.id">
      <RecipieCard class="layout-item-33 layout-item-small-100" :recipie="item" />
    </div>
  </div>
</template>

<script>
import LandingRecipies from "../mock/LandingRecipies.json";
// import RecipieCard from "@components/PageLandingComponents/ReceipieCard";
import RecipieCard from "../components/PageLandingComponents/RecipieCard";

import { fetchAll } from "../services/fileUpload.service";

export default {
  name: "PageLanding",
  components: {
    RecipieCard
  },
  async mounted() {
    this.LandingRecipies = await fetchAll();
  },

  data() {
    return {
      LandingRecipies: null
    };
  }
};
</script>

<style lang="scss" scoped>
.card_container {
  margin: 0 1rem;
}

.page_landing {
  margin-top: 1rem;
}
</style>