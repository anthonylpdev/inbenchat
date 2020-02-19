<template>
  <div class="bubble" :class="{ me: message.userId === this.userId }">
    <img class="avatar"
         src="../assets/avatar-male.jpg"
         width="35"
         height="35"
         title="Sam Jr"
         alt="Sam Jr" />
    <span class="content">{{ message.content }}</span>
  </div>
</template>

<script>
export default {
  name: 'Bubble',
  props: ['message'],
  data() {
    return {
      userId: sessionStorage.getItem('userId'),
    };
  },
};
</script>

<style scoped lang="scss">
  .bubble {
    display: flex;
    flex-direction: row;
    justify-content: flex-start;
    margin-bottom: 20px;
    &.me {
      flex-direction: row-reverse;
      .content {
        background: linear-gradient(93.27deg, #60A9F6 0%, #2A8BF2 100%);
        box-shadow: 10px 10px 50px rgba(42, 139, 242, 0.1),
        15px 15px 35px rgba(42, 139, 242, 0.05),
        10px 10px 25px rgba(42, 139, 242, 0.1);
        border-radius: 10px 10px 0 10px;
        color: #fff;
        margin-left: 0;
        margin-right: 24px;
      }
    }
  }

  .content {
    max-width: 70%;
    margin-left: 24px;
    color: #707C97;
    background: #FFFFFF;
    border: 1px solid rgba(112, 124, 151, 0.25);
    box-sizing: border-box;
    box-shadow: 15px 15px 35px rgba(112, 124, 151, 0.05),
    10px 10px 25px rgba(112, 124, 151, 0.05);
    font-size: 16px;
    line-height: 26px;
    padding: 14px 22px;
    text-align: left;
    border-radius: 0px 10px 10px 10px;
  }

  .avatar {
    border-radius: 50%;
  }
</style>
