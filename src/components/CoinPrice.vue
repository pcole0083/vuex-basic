<template>
  <div id="counter" class="card-panel green lighten-2">
    <div class="p-3">
      <div class="col-10 text-right">
        <h2>
          <i class="fas fa-dollar-sign fa-4x"></i>{{ format(price.amount) }}
        </h2>
        ${{ difference }}
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "CoinPrice",
  computed: {
    price() {
      return this.$store.getters.currentPrice;
    },
    difference() {
      return this.$store.getters.difference;
    }
  },
  methods: {
    format: price => {
      return price.toFixed(2);
    }
  }
};
</script>
