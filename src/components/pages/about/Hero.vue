<template>
  <section class="about__hero">
    <h1 class="about__hero-title">
      Lorem ipsum, dolor sit amet consectetur adipisicing.
    </h1>
    <p class="about__hero-body">
      <span>Lorem ipsum dolor sit.</span>
      <span>Lorem ipsum dolor sit.</span>
      <span>Lorem ipsum dolor sit.</span>
      <span>Lorem, ipsum dolor.</span>
      <span>Lorem, ipsum dolor.</span>
      <span>Lorem, ipsum dolor.</span>
      <span>Lorem ipsum dolor sit.</span>
      <span>Lorem, ipsum dolor.</span>
    </p>
  </section>
</template>

<style lang="postcss" sscoped>
@import '@/assets/styles/variables.css';

.about__hero {
  max-width: 750px;
  padding-top: 145px;
  margin: 0 auto;
  margin-bottom: var(--gap-6);
  &-title {
    margin-bottom: var(--gap-2);
    font-size: 63px;
    line-height: normal;
    text-align: center;
  }
  &-body {
    margin: 0 auto;
    font-size: 25px;
    line-height: 1.5em;
    text-align: center;
    span {
      display: inline-block;
    }
  }
}
</style>
