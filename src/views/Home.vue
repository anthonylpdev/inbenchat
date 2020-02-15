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
  {
    me: true,
    content: 'Il y a quelqu\'un ?',
  },
  {
    me: false,
    content: 'Oui oui ! Bienvenue sur ce chat !',
  },
  {
    me: true,
    content: 'Merci !!',
  },
  {
    me: false,
    content: 'Présente toi en quelques mots ?',
  },
  {
    me: true,
    content: 'Je m\'appelle Sam, je suis de Toulouse et je suis développeur.',
  },
  {
    me: true,
    content: 'Je fais de la photo et de la vidéo depuis plusieurs années.',
  },
  {
    me: false,
    content: 'Super ! Soit le bienvenue Sam !',
  },
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
    height: 80vh;
    width: 850px;
    background-color: #fff;
    padding: 80px;
  }
</style>
