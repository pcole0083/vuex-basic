<template>
  <li class="collection-item">
    <div class="group">
      ${{ formatPrice(price.amount) }}
      <span class="secondary-content">{{
        formatTimestamp(price.timestamp)
      }}</span>
    </div>
  </li>
</template>

<script>
export default {
  name: "PriceItem",
  props: {
    price: Object
  },
  methods: {
    formatTimestamp: timestamp => {
      const date = new Date(timestamp);
      return date.toString().substring(16, 24);
    },
    formatPrice: amount => {
      return amount.toFixed(2);
    }
  }
};
</script>
