<template>
  <div class="w-full flex justify-end">
    <div class="relative w-[100%]">
      <textarea
        v-model="input"
        rows="3"
        class="w-full border border-gray-200 rounded-2xl p-4 pr-20 resize-none focus:outline-none focus:border-primary text-base bg-white"
        placeholder="输入您想与邹韬奋交流的内容..."
        @keydown.enter.prevent="handleSend"
      ></textarea>
      <div class="absolute bottom-4 right-4 flex flex-col items-end space-y-2">
        <button
          class="px-4 h-8 flex items-center justify-center rounded-full bg-primary hover:bg-secondary shadow transition-colors text-white text-sm"
          @click="handleSend"
        >
          发送
        </button>
        <button
          class="px-4 h-8 flex items-center justify-center rounded-full bg-gray-500 hover:bg-gray-600 shadow transition-colors text-white text-sm"
          @click="$emit('clear-messages')"
        >
          清屏
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const input = ref('')

const emit = defineEmits(['send-message', 'clear-messages'])

const handleSend = () => {
  if (input.value.trim()) {
    emit('send-message', input.value)
    input.value = ''
  }
}
</script>

<style scoped>
textarea::-webkit-input-placeholder {
  color: #bdbdbd;
}
textarea:-moz-placeholder {
  color: #bdbdbd;
}
textarea::-moz-placeholder {
  color: #bdbdbd;
}
textarea:-ms-input-placeholder {
  color: #bdbdbd;
}
textarea::placeholder {
  color: #bdbdbd;
}
</style>
