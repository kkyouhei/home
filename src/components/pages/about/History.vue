<template>
  <section class="about__history">
    <div class="history">
      <div class="history-navigation">
        <div class="history-navigation-prev">
          <button @click="Prev">Prev</button>
        </div>
        <div class="history-navigation-next">
          <button @click="Next">Next</button>
        </div>
      </div>
      <div class="history-container">
        <div
          v-for="(year, i) in history"
          :key="i"
          :class="[
            `history-year-${year.label}`,
            { 'active': active === i }
          ]"
        >
          <h2>{{ year.label }}</h2>
          <ul>
            <li
              v-for="(item, j) in year.list"
              :key="j"
              :class="`item-${j}-${year.label}`"
            >
              <template v-if="item.href">
                <a
                  :href="item.href"
                  :title="item.title"
                  :class="{ 'bold': item.bold }"
                >
                  {{ item.title }}
                </a>
              </template>
              <template v-else>
                <span :class="{ 'bold': item.bold }">
                  {{ item.title }}
                </span>
              </template>
            </li>
          </ul>
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
      active: 0
    }
  },
  computed: {
    history() {
      // TODO: mock
      return [
        { 
          label: '2019',
          list : [
            {
              date: '',
              title: 'Lorem ipsum dolor sit',
              href: 'https://example.com',
              bold: true
            },
            {
              date: '',
              title: 'Lorem ipsum dolor sit',
              href: 'https://example.com',
            },
            {
              date: '',
              title: 'Lorem ipsum dolor sit. - Lorem ipsum dolor sit amet.',
              href: 'https://example.com',
            },
            {
              date: '',
              title: 'Lorem ipsum dolor sit',
              href: 'https://example.com',
            },
            {
              date: '',
              title: 'Lorem ipsum dolor sit',
              info: 'https://example.com',
            },
            {
              date: '',
              title: 'Lorem ipsum dolor sit',
              info: 'https://example.com',
              bold: true
            }
          ]
        },
        { 
          label: '2018',
          list : [
            {
              date: '',
              title: 'Lorem ipsum dolor sit',
              href: 'https://example.com',
              bold: true
            },
            {
              date: '',
              title: 'Lorem ipsum dolor sit',
              href: 'https://example.com',
            },
            {
              date: '',
              title: 'Lorem ipsum dolor sit',
              href: 'https://example.com',
            }
          ]
        },
        { 
          label: '2017',
          list : [
            {
              date: '',
              title: 'Lorem ipsum dolor sit',
              href: 'https://example.com',
              bold: true
            },
            {
              date: '',
              title: 'Lorem ipsum dolor sit',
              href: 'https://example.com',
            }
          ]
        }
      ]
    }
  },
  methods: {
    Prev() {
      // TODO: mock
      alert('mockPrev')
    },
    Next() {
      // TODO: mock
      alert('mockNext')
    }
  }
})
</script>

<style lang="postcss" sscoped>
@import '@/assets/styles/variables.css';

.about__history {
  margin-bottom: 240px;
  color: var(--c-black);
  .history {
    &-navigation {
      display: flex;
      &-prev {
        margin-left: auto;
      }
    }
    &-container {
      display: flex;
      overflow: hidden;
      border-bottom-color: var(--c-vue-green);
      border-bottom-style: solid;
      border-bottom-width: 1px;
      h2 {
        margin-bottom: var(--gap-5);
        font-size: 80px;
        line-height: 60px;
        color: var(--c-vue-green);
      }
      div[class^='history-year-'] {
        min-width: 300px;
        padding-right: var(--gap-3);
        padding-bottom: var(--gap-3);
        padding-left: var(--gap-3);
        margin-left: 80px;
        border-left-color: var(--c-vue-green);
        border-left-style: solid;
        border-left-width: 1px;
      }
      h2 {}
      ul {
        column-width: 200px;
        column-count: 2;
        column-gap: 2em;
        li {}
        .active {}
      }
    }
  }
}
</style>
