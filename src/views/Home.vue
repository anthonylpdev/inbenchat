<template>
  <div class="home">
    <div class="head-part"></div>
    <Bubble
      v-for="(message, index) in this.messages"
      :key="index"
      :message="message"
    />
  </div>
</template>

<script>
import Bubble from '../components/Bubble.vue';

const messages = [
  'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid consequatur debitis, dolores et molestiae nam odit quisquam repudiandae sed sit.',
  'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid consequatur debitis, dolores et molestiae nam odit quisquam repudiandae sed sit.',
  'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aliquid consequatur debitis, dolores et molestiae nam odit quisquam repudiandae sed sit.',
];

export default {
  name: 'Home',
  components: {
    Bubble,
  },
  data() {
    return {
      messages,
    };
  },
};
</script>

<style scoped>
  .home {
    float: right;
    height: 80vh;
    width: 850px;
    background-color: #fff;
    padding-left: 50px;
    padding-top: 14px;
    margin-right: 40px;
  }
</style>
