<template>
  <div class="wrapper">
    <slider></slider>
    <purchase></purchase>
  </div>
</template>

<script>

import Slider from '../components/Slider.vue';
import Purchase from '../components/Purchase.vue';

export default {
  components: {
    Slider,
    Purchase,
  },
};
</script>
