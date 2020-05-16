<template>
  <div class="app">
    <router-view/>
  </div>
</template>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@300;400;600;800&display=swap');
  $font-weight-light: 300;
  $font-weight-normal: 400;
  $font-weight-normal: 600;
  $font-weight-black: 800;

  * {
    box-sizing: border-box;
  }
  body
  {
    font-family: 'Montserrat', sans-serif;
    margin: 0;
    padding: 0;
  }
</style>
