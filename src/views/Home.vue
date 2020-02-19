<template>
  <div class="home">
    <div class="inside head-part">
      <img class="avatar"
           src="../assets/avatar-male.jpg"
           width="54"
           height="54"
           :title=this.userName
           :alt=this.userName
      />
      <span class="name">{{ this.userName }}</span>
    </div>
    <div class="inside body-part">
      <Bubble
        v-for="(message, index) in this.listMessages"
        :key="index"
        :message="message"
      />
    </div>
    <div class="inside footer-part">
      <form class="txt" action="" @submit.prevent="send">
        <input type="text" placeholder="Ecrire un message..." v-model="messageToSend">
      </form>
    </div>
  </div>
</template>

<script>
import io from 'socket.io-client';
import Bubble from '../components/Bubble.vue';

export default {
  name: 'Home',
  components: {
    Bubble,
  },
  data() {
    return {
      userName: sessionStorage.getItem('userName'),
      userId: sessionStorage.getItem('userId'),
      messageToSend: '',
      listMessages: [],
      socket: io('localhost:3001'),
    };
  },
  methods: {
    send() {
      this.socket.emit('SEND_MESSAGE', {
        userId: this.userId,
        userName: this.userName,
        content: this.messageToSend,
      });
      this.messageToSend = '';
    },
  },
  mounted() {
    this.socket.on('GET_MESSAGE', (data) => {
      console.log(data);
      this.listMessages = [
        ...this.listMessages,
        data,
      ];
    });
    this.socket.on('NEW_USER', (data) => {
      console.log(data);
    });
    this.socket.on('USER_CREATED', (data) => {
      console.log(data);
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
