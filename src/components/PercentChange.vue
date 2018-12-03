<template>
  <div id="counter" class="card-panel blue lighten-2">
    <div class="p-3">
      <div class="col-2"></div>
      <div class="col-10 text-right">
        <h2>
          <i class="fas fa-percent fa-4x"></i>{{ percentageIncrease }}
          <small>%</small>
        </h2>
        {{ formatTimestamp(currentPrice.timestamp) }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "PercentChange",
  computed: {
    percentageIncrease() {
      return this.$store.getters.percentageIncrease;
    },
    currentPrice() {
      return this.$store.getters.currentPrice;
    }
  },
  methods: {
    formatTimestamp: timestamp => {
      const currentDate = new Date(timestamp);
      return currentDate.toString().substring(16, 24);
    }
  }
};
</script>
