<template>
  <button
    :class="['slider-button', buttonClass]"
    v-on:click="onClick()"
  >
    <icon :name="icon"></icon>
    <span class="sr-only">{{ buttonLabel }}</span>
  </button>
</template>

<script>
import 'vue-awesome/icons'
import Icon from 'vue-awesome/components/Icon.vue'

export default {
  name: 'slider-button',

  components: {
    Icon
  },

  props: [
    'buttonClass',
    'buttonLabel',
    'icon',
    'onClick'
  ]
}

</script>
