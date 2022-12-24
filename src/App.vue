<template>
  <Container>
    <ChatWindow>
      <ChatMessage>
      </ChatMessage>
    </ChatWindow>
  </Container>
</template>

<script>
import Container from "./components/Container.vue";
import ChatWindow from "./components/ChatWindow.vue";
import ChatMessage from "./components/ChatMessage.vue";

export default {
  name: "App",
  components: {
    Container,
    ChatWindow,
    ChatMessage
  },
};
</script>

<style>
body {
  margin: 0;
  background-color: #f9f9fa;
}
</style>