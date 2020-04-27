<template>
  <div class="page_landing">
    <div class="layout page_landing_delete">
      <button v-on:click="toggleDeleteState" class="btn-danger">Delete a recipe</button>
    </div>
    <div class="card_container layout">
      <RecipieCard
        v-for="item in LandingRecipies"
        :key="item.id"
        class="layout-item-33 layout-item-small-100 recipieCard"
        :recipie="item"
        :deleteState="deleteState"
      />
    </div>
  </div>
</template>

<script>
import LandingRecipies from "../mock/LandingRecipies.json";
import RecipieCard from "../components/PageLandingComponents/RecipieCard";

import { fetchAll } from "../services/api.service";

export default {
  name: "PageLanding",
  components: {
    RecipieCard
  },
  async mounted() {
    this.LandingRecipies = await fetchAll();
  },
  methods: {
    toggleDeleteState() {
      this.deleteState = !this.deleteState;
    }
  },

  data() {
    return {
      LandingRecipies: null,
      deleteState: false
    };
  }
};
</script>

<style lang="scss" scoped>
.page_landing_delete {
  justify-content: flex-end;
  margin-right: 1rem;
}

.card_container {
  margin: 0 1rem;
}

.page_landing {
  margin-top: 1rem;
}

.recipieCard {
  margin-bottom: 1rem;
}
</style>