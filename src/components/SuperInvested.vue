<template>
  <section class="super-card">
    <header>
      <h1><img class="logo" src="../assets/images/amp_logo.png" alt="AMP"><span>My super simulator</span></h1>
    </header>

    <h2>How is your super currently invested?</h2>

    <div class="invest-slider">
      <button class="slider-button minus">-</button>
      <div class="slider-holder">
        <vue-slider
          ref="slider"
          v-model="value"
          :data="sliderData"
        ></vue-slider>
      </div>
      <button class="slider-button plus">+</button>
    </div>

    <h3>{{ value }}</h3>
    <p>
      Your aim is for moderate to higher returns primarily from capital growth
      with some income over the long term. Investments are across all asset types,
      with higher exposure to growth assets.
    </p>

    <nav>
      <a href="#" class="button button-back">Back</a>
      <a href="#" class="button button-next">Next</a>
    </nav>
  </section>
</template>

<script>
// to be based on:
// https://www.amp.com.au/super/supersimulator/#!/super-invested

// using
// https://github.com/NightCatSama/vue-slider-component

import vueSlider from 'vue-slider-component'

const data = {
  value: 'Balanced',
  sliderData: [
    'Cash',
    'Conservative',
    'Cautious',
    'Moderately Conservative',
    'Balanced',
    'Moderately Aggressive',
    'Aggressive'
  ]
}

export default {
  name: 'super-invested',

  components: {
    vueSlider
  },

  data: () => {
    return data
  },

  methods: {
    // methods here
  }
}
</script>
