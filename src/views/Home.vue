<template>
  <div class="home">
    <div class="inside head-part">
      <img class="avatar"
           src="../assets/avatar-male.jpg"
           width="54"
           height="54"
           title="Sam Jr"
           alt="Sam Jr"/>
      <span class="name">Sam Jr</span>
    </div>
    <div class="inside body-part">
      <Bubble
        v-for="(message, index) in this.messages"
        :key="index"
        :message="message"
      />
    </div>
    <div class="inside footer-part">
      <form class="txt" action="">
        <input type="text" placeholder="Ecrire un message...">
      </form>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Bubble from '../components/Bubble.vue';

/*
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
*/
const messages = [];

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
  mounted() {
    axios.get('http://localhost:3030/message')
      .then((response) => {
        this.messages = response.data.data;
      });
  },
};


</script>

<style scoped lang="scss">
  .home {
    width: 850px;
    background-color: #fff;
    .inside {
      padding: 0 60px;
    }
    .head-part {
      display: flex;
      flex-direction: column;
      height: 140px;
      background: #FAFBFF;
      border-radius: 6px 6px 0px 0px;
      justify-content: center;
      align-items: center;
      text-align: center;
      .avatar {
        display: block;
        border-radius: 50%;
        margin-bottom: 2px;
      }
      .name {
        font-weight: bold;
      }
    }
    .body-part {
      height: 500px;
      overflow-y: scroll;
      padding-top: 40px;
      padding-bottom: 40px;
    }
    .footer-part {
      .txt {
        height: 98px;
        display: block;
        width: 100%;
        border-top: 2px solid #f2f2f2;
        input {
          display: block;
          width: 100%;
          border: none;
          font-family: Avenir, Helvetica, Arial, sans-serif;
          padding: 27px 20px;
          text-align: left;
          font-size: 20px;
          line-height: 24px;
          &:focus {
            outline: none;
          }
        }
      }
    }
  }
</style>
