<template>
  <Container>
    <ChatWindow>
      <ChatMessage v-for="message in messages" :key="message.id">
        <template #username> {{ message.author }} </template>
        <template #time> {{ message.datetime }} </template>
        <template #text> {{ message.text }} </template>
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
  methods: {
    loadMessages(){
      this.axios.get("https://61bcd385d8542f0017824a2a.mockapi.io/messages")
      .then((responce) => {
        let messages = responce.data;
        messages.forEach(element => {
          let message = {
            author: element.author,
            datetime: element.datetime,
            text: element.text,
            id: element.id,
          };
          this.messages.push(message);
        });
      });
    }
  },
  data(){
    return{
      messages: [],
    }
  },
  mounted(){
    this.loadMessages();
  }

};
</script>

<style>
body {
  margin: 0;
  background-color: #f9f9fa;
}
</style>