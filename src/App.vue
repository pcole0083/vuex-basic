<template>
  <div id="app" class="grid">
    <header class="row" data-area="header">
      <div class="col-12"><h1>Dashboard</h1></div>
    </header>
    <section class="col-sm-6" data-area="col1"><CoinPrice /></section>
    <section class="col-sm-6" data-area="col2"><PercentChange /></section>
    <section class="card-panel" data-area="colfull">
      <ul class="collection with-header">
        <li class="collection-header"><h4>Price History</h4></li>
        <PriceItem
          v-bind:key="price.timestamp"
          v-for="price in prices"
          v-bind:price="price"
        />
      </ul>
    </section>
  </div>
</template>

<script>
//Components
import CoinPrice from "./components/CoinPrice.vue";
import PercentChange from "./components/PercentChange.vue";
import PriceItem from "./components/PriceItem.vue";
//Store
import store, { actions } from "./store";

export default {
  name: "app",
  components: {
    CoinPrice,
    PercentChange,
    PriceItem
  },
  store,
  computed: {
    prices() {
      return store.state.prices;
    }
  },
  created: function() {
    setInterval(this.triggerNewPrice, 3000);
  },
  methods: {
    triggerNewPrice: () => {
      const diff = (Math.random() - Math.random()) * 10;
      const randomNewPrice = store.getters.currentPrice.amount + diff;
      store.commit(actions.UPDATE_PRICE, {
        amount: randomNewPrice,
        timestamp: Date.now()
      });
    }
  }
};
</script>
