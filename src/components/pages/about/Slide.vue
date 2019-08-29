<template>
  <section class="about__slider">
    <div class="slider">
      <div class="slider-container">
        <div
          v-for="(slide, i) in slides"
          :key="i"
          :class="[
            `slide-item-${i}`,
            { 'active': active === i },
            { 'next': next === i },
            { 'after': after === i }
          ]"
        >
          <img
            class="slide-image"
            :src="slide.src"
            :srcset="slide.srcset"
            :alt="slide.label"
          />
          <div  
            class="slide-label"
            v-html="slide.label"
          />
        </div>
      </div>
      <div class="slider-navigation">
        <div class="slider-navigation-bullet">
          <button
            v-for="(slide, j) in slides"
            :key="j"
            class="slider-navigation-bullet-dot"
            :class="[
              { 'active': active === j },
            ]"
            @click="select(j)"
            v-html="j+1"
          />
        </div>
        <div class="slider-navigation-prev">
          <button @click="Prev" title="Prev">Prev</button>
        </div>
        <div class="slider-navigation-next">
          <button @click="Next" title="Next">Next</button>
        </div>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import Vue from 'vue';

export default Vue.extend({
  data() {
    return {
      active: 0,
      next: 1,
      after: 2
    }
  },
  computed: {
    slides() {
      // TODO: mock
      return [
        {
          src: 'http://placehold.jp/1000x600.png?text=1',
          srcset: 'http://placehold.jp/1000x600.png?text=1 1x, http://placehold.jp/2000x1200.png?text=1 2x',
          label: 'Lorem ipsum dolor sit. - Lorem ipsum dolor sit amet.Lorem ipsum dolor sit. - Lorem ipsum dolor sit amet.Lorem ipsum dolor sit. - Lorem ipsum dolor sit amet.Lorem ipsum dolor sit. - Lorem ipsum dolor sit amet.Lorem ipsum dolor sit. - Lorem ipsum dolor sit amet.Lorem ipsum dolor sit. - Lorem ipsum dolor sit amet.'
        },
        {
          src: 'http://placehold.jp/1000x600.png?text=2',
          srcset: 'http://placehold.jp/1000x600.png?text=2 1x, http://placehold.jp/2000x1200.png?text=2 2x',
          label: 'Lorem ipsum dolor sit. - Lorem ipsum dolor sit amet.'
        },
        {
          src: 'http://placehold.jp/1000x600.png?text=3',
          srcset: 'http://placehold.jp/1000x600.png?text=3 1x, http://placehold.jp/2000x1200.png?text=3 2x',
          label: 'Lorem ipsum dolor sit. - Lorem ipsum dolor sit amet.'
        },
        {
          src: 'http://placehold.jp/1000x600.png?text=4',
          srcset: 'http://placehold.jp/1000x600.png?text=4 1x, http://placehold.jp/2000x1200.png?text=4 2x',
          label: 'Lorem ipsum dolor sit. - Lorem ipsum dolor sit amet.'
        },
        {
          src: 'http://placehold.jp/1000x600.png?text=5',
          srcset: 'http://placehold.jp/1000x600.png?text=5 1x, http://placehold.jp/2000x1200.png?text=5 2x',
          label: 'Lorem ipsum dolor sit. - Lorem ipsum dolor sit amet.'
        }
      ]
    }
  },
  methods: {
    Prev() {
      const num = this.slides.length
      this.select(this.active - 1)
      if (this.active === -1) {
        this.select(num - 1)
      }
    },
    Next() {
      const num = this.slides.length
      this.select(this.active + 1)
      if (this.active === num) {
        this.select(0)
      }
    },
    select(i: number) {
      const num = this.slides.length
      this.active = i
      this.next = i + 1
      this.after = i + 2
      if (num === i + 2) {
        this.after = 0
      }
      if (num === i + 1) {
        this.next = 0
        this.after = 1
      }
    }
  }
})
</script>

<style lang="postcss" sscoped>
@import '@/assets/styles/variables.css';

.slider {
  position: relative;
  width: 1000px;
  margin-right: auto;
  margin-bottom: 188px;
  margin-left: auto;
  &-container {
    position: relative;
    margin-bottom: 83px;
    div[class^='slide-item-'] {
      position: absolute;
      top: 60px;
      left: 0;
      width: 1000px;
      height: 100%;
      overflow: hidden;
      border-radius: 10px;
      box-shadow: var(--shadow-depth-5);
      opacity: 0;
      transition: all 0.5s;
      transform: scale(0.93);
      &.active {
        position: relative;
        top: 0;
        z-index: 3;
        opacity: 1;
        transform: scale(1);
        .slide-label {
          position: absolute;
          bottom: 0;
          left: 0;
          display: block;
          width: 100%;
          padding: var(--gap-2);
          font-size: var(--font-size-xs);
          color: var(--c-white);
          background: rgba(0, 0, 0, 0.5);
        }
      }
      &.next {
        top: 28px;
        z-index: 2;
        opacity: 1;
        transform: scale(0.97);
        &::after {
          position: absolute;
          top: 0;
          left: 0;
          display: block;
          width: 100%;
          height: 100%;
          content: '';
          background-color: rgba(255, 255, 255, 0.5);
        }
      }
      &.after {
        top: 60px;
        z-index: 1;
        opacity: 1;
        transform: scale(0.93);
        &::after {
          position: absolute;
          top: 0;
          left: 0;
          display: block;
          width: 100%;
          height: 100%;
          content: '';
          background-color: rgba(255, 255, 255, 0.5);
        }
      }
      .slide-label {
        display: none;
      }
    }
  }
  &-navigation {
    &-bullet {
      display: flex;
      justify-content: center;
      &-dot {
        width: 65px;
        height: 3px;
        margin-left: var(--gap-2);
        font-size: 0;
        background-color: var(--c-gray-lighter);
        border-radius: 2px;
        &:first-child {
          margin-left: 0;
        }
        &.active {
          background-color: var(--c-vue-green);
        }
      }
    }
    &-next {
      right: 0;
    }
    &-prev {
      left: 0;
    }
    &-next,
    &-prev {
      position: absolute;
      top: 0;
      z-index: 5;
      width: 50%;
      height: 600px;
      button {
        width: 100%;
        height: 100%;
        font-size: 0;
      }
    }
  }
}
</style>
