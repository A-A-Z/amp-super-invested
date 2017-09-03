<template>
  <section class="super-card">
    <header>
      <h1>
        <img class="logo" src="../assets/images/amp_logo.png" alt="AMP">
        <span>My super simulator</span>
      </h1>
    </header>

    <h2>How is your super currently invested?</h2>

    <div class="invest-slider">
      <slider-button
        button-class="minus"
        button-label="Slider minus one"
        icon="minus"
        :on-click="sliderBack"
      ></slider-button>
      <div class="slider-holder">
        <vue-slider
          ref="slider"
          v-model="sliderValue"
          :data="sliderData"
        ></vue-slider>
      </div>
      <slider-button
        button-class="plus"
        button-label="Slider plus one"
        icon="plus"
        :on-click="sliderForward"
      ></slider-button>
    </div>

    <p>
      <strong>{{ sliderValue }}:</strong> {{ investmentOptions[indexedOptions[sliderValue]].summary }}
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
import 'vue-awesome/icons'
import Icon from 'vue-awesome/components/Icon.vue'
import SliderButton from './SliderButton'

const data = {
  sliderValue: '',
  sliderData: [
    'Cash',
    'Conservative',
    'Cautious',
    'Moderately Conservative',
    'Balanced',
    'Moderately Aggressive',
    'Aggressive'
  ],
  investmentOptions: [],
  indexedOptions: {}
}

export default {
  name: 'super-invested',

  components: {
    vueSlider,
    Icon,
    SliderButton
  },

  data: () => {
    return data
  },

  props: [
    'configId',
    'defaultValue'
  ],

  beforeMount () {
    const jsonData = JSON.parse(document.getElementById(this.configId).innerHTML)
    console.log('beforeMount', jsonData)

    this.investmentOptions = jsonData.investmentOptions
    this.sliderData = this.formatSliderData(jsonData.investmentOptions)
    this.sliderValue = this.defaultValue
  },

  methods: {
    formatSliderData (options) {
      let formatedOptions = []

      for (let [index, option] of options.entries()) {
        formatedOptions.push(option.name)
        this.indexedOptions[option.name] = index
        // console.log(index)
      }

      return formatedOptions
    },

    getValueIndex () {
      return this.sliderData.indexOf(this.sliderValue)
    },

    sliderBack () {
      let valueIndex = this.getValueIndex()
      if (valueIndex > 0) {
        valueIndex--
      }
      this.sliderValue = this.sliderData[valueIndex]
    },

    sliderForward () {
      let valueIndex = this.getValueIndex()
      if (valueIndex < this.sliderData.length) {
        valueIndex++
      }
      this.sliderValue = this.sliderData[valueIndex]
    }
  }
}
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Open+Sans:400,600|Scope+One');
  @import '../assets/styles/app.scss'
</style>
