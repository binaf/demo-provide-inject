<script>
import uniqid from "uniqid";

export default {
  render() {
    return this.$slots.default;
  },
  data() {
    return {
      color: null,
      availableColors: ["red", "blue", "green", "purple"],
      uniqid: null,
    };
  },
  provide() {
    return {
      cardColorApi: {
        getColor: () => this.color,
        setColor: (color) => {
          if (null === color || this.availableColors.includes(color)) {
            this.color = color;
          }

          this.uniqid = uniqid();
        },
        getAvailableColors: () => this.availableColors,
        getUniqid: () => this.uniqid,
      },
    };
  },
};
</script>
