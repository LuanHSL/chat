<script>
export default {
  name: 'SendInput',
  emits: ['sendMessage'],
  data() {
    return {
      writtenMessage: '',
    };
  },
  methods: {
    sendMessage() {
      if (this.writtenMessage) {
        this.$emit('sendMessage', this.writtenMessage);
        this.clearWrittenMessage();
      }
    },
    clearWrittenMessage() {
      this.writtenMessage = '';
    },
  },
};

</script>

<template>
  <div class="flex items-center space-x-3 px-4 fixed bottom-0 right-0 bg-blue-700 w-full h-[80px] rounded-t-[20px]">
    <input
      v-model="writtenMessage"
      type="text" class="px-2 w-full outline-0 rounded-[20px] h-[35px]"
      @keyup.enter="sendMessage"
    >
    <button
      v-show="writtenMessage"
      class="bg-blue-400 hover:bg-blue-500 px-4 rounded-[10px] h-[35px] text-white font-semibold"
      @click="sendMessage"
    >
      Send
    </button>
  </div>
</template>
