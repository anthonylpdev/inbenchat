<template>
  <div class="bubble">{{ message }}</div>
</template>

<script>
export default {
  name: 'Bubble',
  props: ['message'],
};
</script>

<style scoped>
  .bubble {
    max-width: 70%;
    background: linear-gradient(93.27deg, #60A9F6 0%, #2A8BF2 100%);
    /* Shadow Block Message My Opponent */
    box-shadow: 10px 10px 50px rgba(42, 139, 242, 0.1),
    15px 15px 35px rgba(42, 139, 242, 0.05),
    10px 10px 25px rgba(42, 139, 242, 0.1);
    border-radius: 0px 10px 10px 10px;
    color: #fff;
    font-size: 16px;
    line-height: 26px;
    padding: 14px 22px 25px;
    text-align: left;
    margin-bottom: 15px;
  }
</style>
