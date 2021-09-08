<template>
  <div class="card-color-selector">
    <CardColorButton
      v-for="(color, index) in availableColors"
      :key="`color-${index}`"
      :color="color"
    >
      {{ color }}
    </CardColorButton>
    <a
      class="card-color-selector-reset"
      href="#"
      v-if="cardColorApi.getColor() !== null"
      @click.prevent="reset()"
      >Reset</a
    >
  </div>
</template>

<script>
import CardColorButton from "./CardColorButton";
export default {
  components: {
    CardColorButton,
  },
  inject: ["cardColorApi"],
  computed: {
    availableColors() {
      return this.cardColorApi.getAvailableColors();
    },
  },
  methods: {
    reset() {
      this.cardColorApi.setColor(null);
    },
  },
};
</script>

<style scoped>
.card-color-selector {
  display: flex;
  justify-content: center;
}

.card-color-button:not(:last-child) {
  margin-right: 10px;
}

.card-color-selector-reset {
  color: white;
}
</style>
