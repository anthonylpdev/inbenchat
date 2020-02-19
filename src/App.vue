<template>
  <div id="app">
    <div class="container">
      <router-view/>
    </div>
  </div>
</template>

<style lang="scss">
  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    width: 100vw;
    height: 100vh;
    background-color: #f2f2f2;
    position: absolute;
    left: 0;
    top: 0;
  }

  .container {
    display: flex;
    justify-content: center;
    padding-top: 60px;
  }

</style>
