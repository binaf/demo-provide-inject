<script>
export default {
  render() {
    return this.$slots.default;
  },
  inject: ["cardColorApi"],
  computed: {
    uniqid() {
      return this.cardColorApi.getUniqid();
    },
    color() {
      return this.cardColorApi.getColor();
    },
  },
  watch: {
    uniqid(val) {
      console.log(this.color);
    },
  },
};
</script>
