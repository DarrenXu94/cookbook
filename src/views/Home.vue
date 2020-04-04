<template>
  <div class="home">
    <PageLanding />
  </div>
</template>

<script>
// @ is an alias to /src
import PageLanding from "@/components/PageLanding.vue";

export default {
  name: "Home",
  components: {
    PageLanding
  }
};
</script>
