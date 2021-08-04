<template>
  <div class="slider__item" v-show="selectedItem === item.id">
    <div class="slider__pic">
      <img :src="item.pic" alt="sliderPic" class="slider__pic-img">
      <div class="slider__pic-elem">{{item.number}}</div>
    </div>
    <div class="slider__desk">
      <div class="slider__headline">{{item.headline}}</div>
      <p class="slider__text">{{item.text}}</p>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    item: {
      type: Object,
      default: () => {},
    },
    selectedItem: {
      type: Number,
    },
  },
};
</script>

<style lang="scss" scoped>

  .slider__item {
    padding: 50px 50px;
    background: #fff;
    border-radius: 10px;
    box-shadow: 0px 0px 40px rgba(0, 0, 0, 0.1);
    margin: 0px 20px;
    min-height: 455px;
  }

  .slider__pic {
    width: 550px;
    position: relative;
    overflow: hidden;
    margin: 0 auto;

    &-elem {
      position: absolute;
      top: -3px;
      left: -12px;
      background: #fff;
      border-radius: 50%;
      width: 50px;
      height: 50px;
      display: flex;
      justify-content: center;
      align-items: center;
      color: #7DB945;
      font-weight: 700;
    }
  }

  .slider__desk {
    text-align: center;
  }

  .slider__headline {
    font-weight: 700;
    margin-bottom: 12px;
  }
</style>
