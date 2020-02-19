<template>
  <div class="login">
    <div class="inside body-part">
      <h1>Connexion</h1>
      <form class="form" @submit.prevent="login" action="">
        <label for="name">Nom</label>
        <input required id="name" type="text" class="default" v-model="name">
        <input type="submit" value="Se connecter" class="submit">
      </form>
    </div>
  </div>
</template>

<script>

import io from 'socket.io-client';

export default {
  name: 'Login',
  methods: {
    login() {
      this.socket.emit('ADD_USER', {
        name: this.name,
      });
    },
  },
  data() {
    return {
      name: '',
      socket: io('localhost:3001'),
    };
  },
  mounted() {
    this.socket.on('USER_CREATED', (data) => {
      sessionStorage.setItem('userName', this.name);
      sessionStorage.setItem('userId', data);
      this.$router.push('/');
    });
  },
};

</script>

<style scoped lang="scss">
  .login {
    display: flex;
    width: 850px;
    background-color: #fff;
    padding: 40px 0;
    justify-content: center;
    .inside {
      width: 400px;
      h1 {
        display: block;
        margin-bottom: 40px;
      }
      .form {
        //display: flex;
        label {
          display: block;
          margin-bottom: 8px;
        }
        input {
          display: block;
          height: 32px;
          margin: 0 auto 24px;
          width: 100%;
          background: #FCFDFE;
          border: 1px solid #F0F1F7;
          box-sizing: border-box;
          border-radius: 8px;
          &[type="submit"]{
            max-width: 200px;
            color: #fff;
            margin-top: 60px;
            background: linear-gradient(100.61deg, #7CB8F7 0%, #2A8BF2 100%);
            box-shadow: 10px 6px 25px rgba(42, 139, 242, 0.15),
            4px 4px 25px rgba(42, 139, 242, 0.05),
            6px 6px 25px rgba(42, 139, 242, 0.15);
            border-radius: 6px;
            &:hover {
              cursor: pointer;
            }
          }
        }
      }
    }
  }
</style>
