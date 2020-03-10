<template>
  <div 
    :class='{"chat-message--self": isOwnMessage,
             "chat-message--other": !isOwnMessage}'
  >
    <span class="chat-message__sender" > 
        {{ message.sender.charAt(0) }} 
    </span>
    <div class="chat-message_content">
      {{ message.content }}
    </div>
  </div>
</template>
<script>
export default {
  props: {
    message: Object
  },
  computed: {
    isOwnMessage() {
      return (this.message.sender === "Me");
    }
  }
};
</script>
<style lang="scss" scoped>
.chat-message--self, .chat-message--other {
  width: 100%;
  margin: 5px;
  position: relative;
}

.chat-message__sender {
    width: 40px;
    height: 40px;
    background-color: #6c5ce7;
    color: white;
    text-align: center;
    vertical-align: middle;
    line-height: 40px;
    font-weight: bold;
    font-size: 1em;
    border-radius: 5px;
    position: absolute;
    bottom: 0;
}

.chat-message_content {
  position: relative;
  max-width: calc(100% - 50px);
  border-radius: 5px;
  display: inline-block;
  padding: 20px;
  max-width: 50%;
}

.chat-message--other {
    text-align: left;

    .chat-message__sender {
        left: 0;
    }

    .chat-message_content {
        margin-left: 50px;
        margin-right: 0;
        background-color: #eee;
        color: 333;
    }

}




.chat-message--self {
    text-align: right;
    width: 100%;
    
    .chat-message__sender {
        right: 0;
        background-color: #74b9ff;
    }

    .chat-message_content {
        margin-left: 0;
        margin-right: 50px;
        background-color: #74b9ff;
        color: white;
        text-align: left;
    }
}


</style>
