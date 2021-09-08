<template>
  <div>
    <h1>Demo provide/inject</h1>

    <div class="cards-container">
      <CardColorProvider v-if="true">
        <Card title="Card with color provider" />
      </CardColorProvider>

      <CardColorProvider v-if="true">
        <Card
          title="Card with color provider and change listener"
          :change-color-listener="true"
        />
      </CardColorProvider>

      <Card title="Card without color provider" v-if="false" />
    </div>
  </div>
</template>

<script>
import Card from "./Card.vue";
import CardColorProvider from "./CardColorProvider.vue";
export default {
  components: {
    Card,
    CardColorProvider,
  },
};
</script>

<style scoped>
.cards-container {
  display: flex;
  justify-content: space-between;
}
</style>
