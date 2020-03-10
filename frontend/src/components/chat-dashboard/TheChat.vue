<template>
  <div class="chat pure-u-md-3-4">
    <div class="chat-header">
      <h2> {{ conversation.name }} </h2>
    </div>
    <div class="chat-content" ref='chatContent'>
      <message v-for='message in messages' :key='message.id' :message='message' />
    </div>
    <div class="chat-send pure-g">
      <message-input @send='sendMessage($event)' />
    </div>
  </div>
</template>
<script>
import Message from "./chat-elements/ChatMessage.vue";

import MessageInput from "./chat-elements/MessageInput.vue";

export default {
  components: {
    Message,
    MessageInput
  },
  data() {
    return {
      conversation: {
        name: 'CS1530 Project'
      },
      messages: [
        {
          sender: 'S Maribojoc',
          content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum'
        },
        {
          sender: 'Me',
          content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum'
        },
        {
          sender: 'D Maribojoc',
          content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum'
        },
        {
          sender: 'P Maribojoc',
          content: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in culpa qui officia deserunt mollit anim id est laborum'
        }
      ]
    }
  },
  methods: {
    sendMessage (message) {
      this.messages.push(message)
      this.$nextTick(() => { // wait until the DOM renders with the new message
        this.$refs.chatContent.scrollTop = this.$refs.chatContent.scrollHeight;
      })
      
    }
  }
};
</script>
<style lang="scss" scoped>
.chat {
  height: 100%;
}

.chat-header {
  height: 50px;
  background-color: #fff;
  line-height: 50px;
  padding: 0 30px;

  h2 {
    font-weight: bold;;
  }
}

.chat-content {
  height: calc(100% - 120px);
  padding: 0 5%;
  overflow: scroll;
}

.chat-send {
  background-color: #eee;
  height: 70px;
  padding: 15px 20px;
  text-align: center;
}
</style>
