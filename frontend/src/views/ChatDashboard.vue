<template>
  <div class="chat-dashboard pure-g">
    <the-sidebar />
    <the-chat />
  </div>
</template>

<script>
import TheSidebar from "@/components/chat-dashboard/TheSidebar.vue";
import TheChat from "@/components/chat-dashboard/TheChat.vue";

export default {
  name: "Home",
  components: {
    TheChat,
    TheSidebar
  }
};
</script>
<style lang="scss" scoped>
.chat-dashboard {
  background-color: #fafafa;
  width: 100%;
  height: 100vh;
}
</style>
