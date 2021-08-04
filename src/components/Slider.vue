<template>
  <section class="slider">
    <div class="container">
      <div class="slider__container">
          <a href="#" class="slider__btn" @click.prevent="prevSlide">
            <svg class="slider__btn-pic" width="24" height="44" viewBox="0 0 24 44" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M22 2L2 22L22 42"
                stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </a>
          <slider-item
              v-for="item in items"
              :key="item.id"
              :item="item"
              :selectedItem="currentItemIndex">
          </slider-item>
          <a href="#" class="slider__btn slider__btn--next" @click.prevent="nextSlide">
            <svg class="slider__btn-pic" width="24" height="44" viewBox="0 0 24 44" fill="none" xmlns="http://www.w3.org/2000/svg">
              <path d="M22 2L2 22L22 42"
                stroke-width="3" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
          </a>
      </div>
    </div>
  </section>
</template>

<script>
import exactly from '@/assets/images/exactly.png';
import fresh from '@/assets/images/fresh.png';
import carefully from '@/assets/images/carefully.png';
import delivery from '@/assets/images/delivery.png';
import effectively from '@/assets/images/effectively.png';

import SliderItem from './SliderItem.vue';

export default {
  components: {
    SliderItem,
  },
  data() {
    return {
      items: [
        {
          id: 0,
          pic: exactly,
          headline: 'Привезём точно по списку',
          text: 'Сборщик берëт с собой наручный терминал, на котором он видит весь список покупок для каждого заказа.',
          number: 1,
        },
        {
          id: 1,
          pic: effectively,
          headline: 'Собираем быстро и эффективно',
          text: 'Для улучшения эргономики пространства товары размещены от тяжëлых к лëгким, находящимся уже в конечной зоне упаковки.',
          number: 2,
        },
        {
          id: 2,
          pic: delivery,
          headline: 'За свежесть и качество отвечаем',
          text: 'Выделены специальные зоны, в том числе холодная и морозильная.',
          number: 3,
        },
        {
          id: 3,
          pic: fresh,
          headline: 'Шампунь не положат рядом с рыбой',
          text: 'Собираем и упаковываем ваш заказ с заботой: соблюдаем принципы товарного соседства и учитываем вес товара.',
          number: 4,
        },
        {
          id: 4,
          pic: carefully,
          headline: 'Довезëм в сохранности даже яйца',
          text: 'Бережно транспортируем контейнеры, фиксируя их стяжными ремнями. Системы охлаждения поддерживают температурный режим.',
          number: 5,
        },

      ],
      currentItemIndex: 0,
    };
  },
  methods: {
    nextSlide() {
      const newItemIndex = this.currentItemIndex + 1;
      if (newItemIndex > this.items.length - 1) {
        this.currentItemIndex = 0;
      } else {
        this.currentItemIndex = newItemIndex;
      }
    },
    prevSlide() {
      const newItemIndex = this.currentItemIndex - 1;
      if (newItemIndex < 0) {
        this.currentItemIndex = this.items.length - 1;
      } else {
        this.currentItemIndex = newItemIndex;
      }
    },
  },
};
</script>

<style lang="scss" scoped>
.slider {
  background: beige;
  padding: 50px 0;

  &__container {
    display: flex;
    justify-content: center;
    align-items: center;
    max-width: 650px;
    margin: 0 auto;
  }

  &__btn--next {
    transform: rotateY(180deg);
  }

  &__btn-pic {
    stroke: #D0D4CD;
    transition: stroke .3s;

    &:hover {
      stroke: black;
      transition: stroke .3s;
    }
  }
}
</style>
