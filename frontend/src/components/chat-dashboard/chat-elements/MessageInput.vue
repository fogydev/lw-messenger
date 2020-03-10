<template>
  <div class="message-wrapper">
    <!-- PROFILE IMAGE -->
    <div class="user-image">
      <img
        src="https://pbs.twimg.com/profile_images/1220885585943986177/zCV7oihl_400x400.jpg"
      />
    </div>
    <!-- SEND MESSAGE -->
    <div class="message-input">
      <input
        class="pure-u-md-4-5"
        type="text"
        placeholder="Type a message..."
        v-model="currentMessage"
        @keydown.enter="sendMessage"
      />
      <div class="message-input__add-on">
        <i class="fas fa-image"></i>
      </div>
      <div class="message-input__add-on">
        <i class="fas fa-link"></i>
      </div>
      <div class="message-input__add-on">
        <i class="fas fa-at"></i>
      </div>
    </div>

    <!-- SEND BUTTON -->
    <div class="send-message">
      <i class="fas fa-paper-plane" @click="sendMessage"></i>
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
        currentMessage: ""
    }
  },
  methods: {
    sendMessage() {
      if (this.currentMessage.length === 0) {
        return;
      }
      this.$emit('send', {
        sender: "Me",
        content: this.currentMessage
      });
      this.currentMessage = "";
    }
  }
};
</script>
<style lang="scss" scoped>
.message-wrapper {
  display: block;
  overflow: hidden;
  width: 90%;
  margin: 0 auto;
  height: 40px;
}

.user-image {
  min-width: 50px;
  display: inline-block;
  height: 100%;
  float: left;

  img {
    height: 100%;
    width: auto;
    border-radius: 5px;
  }
}

.message-input {
  width: calc(100% - 140px);
  display: inline-block;
  margin: 0;
  height: 40px;
  padding: 5px 15px;
  border-radius: 5px;
  background-color: #fff;
  line-height: 30px;
}

.message-input__add-on {
  width: 20px;
  height: 20px;
  margin-right: 8px;
  color: #aaa;
  cursor: pointer;
  display: inline-block;

  :hover {
    color: #636e72;
  }
}

input[type="text"] {
  width: calc(100% - 84px);
  padding-right: 10px;
  height: 100%;
  outline: none;
  font-size: 0.9em;
  border: none;
}

.send-message {
  float: right;
  display: inline-block;
  width: 40px;
  height: 40px;
  line-height: 40px;
  font-size: 1.2em;
  color: white;
  border-radius: 5px;
  background-color: #0984e3;
  cursor: pointer;
}
</style>
