<template>
    <div id="app" class="default-background-color">
      <nuxt />
    </div>
</template>

<style lang="sass">
  #app
    width: 100vw
    height: 100vh
    overflow: auto
  .default-background-color
    background-color: #F6E6E6
  .logo
    font-family: 'Pacifico', cursive
    &:before
      content: 'bridge'
      font-size: 24px
      color: #414141
  .--text--big
    font-size: 18px
  .--text--middle
    font-size: 15px
  .--text--small
    font-size: 12px
  .--text--micro
    font-size: 9px
  .--bold--400
    font-weight: 400
  .--bold--600
    font-weight: 600
  .--bold--800
    font-weight: 800

</style>
