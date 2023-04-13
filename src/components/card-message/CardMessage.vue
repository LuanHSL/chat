<script>
export default {
  name: 'CardMessage',
  props: {
    isSender: {
      type: Boolean,
      default: false,
    },
    content: String,
  },
};

</script>

<template>
  <div :class="{'flex justify-end': isSender}">
    <div
      class="w-fit p-2 max-w-[80%]"
      :class="{
        'bg-gray-100 rounded-b-[10px] rounded-r-[10px]': !isSender,
        'bg-violet-800 rounded-b-[10px] rounded-l-[10px] text-white': isSender,
      }"
    >
      {{ content }}
    </div>
  </div>
</template>
