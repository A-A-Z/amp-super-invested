<template>
  <section class="super-card">
    <header>
      <h1><img class="logo" src="../assets/images/amp_logo.png" alt="AMP"><span>My super simulator</span></h1>
    </header>

    <h2>How is your super currently invested?</h2>
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

const data = {
  test: 1
}

export default {
  name: 'super-invested',

  data: () => {
    return data
  },

  methods: {
    // methods here
  }
}
</script>
