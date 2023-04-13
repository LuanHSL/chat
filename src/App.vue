<script>
import { defineAsyncComponent } from 'vue';
const SendInput = defineAsyncComponent(() => import('./components/send-input/SendInput.vue'));
const CardMessage = defineAsyncComponent(() => import('./components/card-message/CardMessage.vue'));

export default {
  name: 'App',
  components: {
    SendInput,
    CardMessage,
  },
  data() {
    return {
      senderId: 2,
      messages: [{
        senderId: 1,
        content: 'ola meu amigo, tudo bem?',
      }],
    };
  },
  methods: {
    sendMessage(content) {
      this.messages.push({
        senderId: this.senderId,
        content,
      });
    },
  },
};
</script>

<template>
  <div class="flex flex-col space-y-2 p-3 pb-[95px] h-screen">
    <CardMessage
      v-for="message in messages"
      :key="message.senderId"
      :content="message.content"
      :is-sender="senderId === message.senderId"
    />
  </div>
  <SendInput @send-message="sendMessage" />
</template>
