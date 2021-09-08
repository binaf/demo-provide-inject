<template>
  <div :class="['card', color && `card--color-${color}`]">
    <h2 class="card-title">{{ title }}</h2>
    <CardColorSelector v-if="cardColorApi" />
    <CardColorChangeListener v-if="changeColorListener" />
  </div>
</template>

<script>
import CardColorSelector from "./CardColorSelector";
import CardColorChangeListener from "./CardColorChangeListener";

export default {
  components: { CardColorSelector, CardColorChangeListener },
  props: {
    title: {
      type: String,
      required: true,
    },
    changeColorListener: {
      type: Boolean,
      default: false,
    },
  },
  inject: {
    cardColorApi: {
      default: null,
    },
  },
  computed: {
    color() {
      return this.cardColorApi ? this.cardColorApi.getColor() : null;
    },
  },
};
</script>

<style scoped>
.card {
  border: 1px solid grey;
  color: black;
  border-radius: 5px;
  padding: 10px;
}

.card--color-red {
  background: red;
  color: white;
}

.card--color-blue {
  background: blue;
  color: white;
}

.card--color-green {
  background: green;
  color: white;
}

.card--color-purple {
  background: purple;
  color: white;
}
</style>