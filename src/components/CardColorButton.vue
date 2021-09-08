<template>
  <a
    href="#"
    :class="['card-color-button', active && `card-color-button--active`]"
    @click.prevent="handleClick()"
    :style="`background-color: ${color}`"
    :title="color"
  ></a>
</template>

<script>
export default {
  props: {
    color: {
      type: String,
      required: true,
    },
  },
  inject: ["cardColorApi"],
  computed: {
    active() {
      return this.cardColorApi.getColor() === this.color;
    },
  },
  methods: {
    handleClick() {
      this.$emit("click");
      this.cardColorApi.setColor(this.color);
    },
  },
};
</script>

<style scoped>
.card-color-button {
  border-radius: 50px;
  width: 20px;
  height: 20px;
  display: inline-block;
}
.card-color-button--active {
  border: 1px solid black;
}
</style>