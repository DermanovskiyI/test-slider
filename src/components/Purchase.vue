<template>
  <section class="purchase">
    <div class="container">
      <button type="button" @click="togglePopup" class="btn">К покупкам</button>
    </div>
    <purchase-popup v-if="isPopupShown" @togglePopup="togglePopup"/>
  </section>
</template>

<script>
import PurchasePopup from './PurchasePopup.vue';

export default {
  components: {
    PurchasePopup,
  },
  data() {
    return {
      isPopupShown: false,
    };
  },
  methods: {
    togglePopup() {
      this.isPopupShown = !this.isPopupShown;
    },
  },
};
</script>

<style lang="scss" scoped>
.btn {
  background: #7DB945;
  border: none;
  border-radius: 10px;
  width: 340px;
  padding: 15px;
  cursor: pointer;
  color: #fff;
}
</style>
