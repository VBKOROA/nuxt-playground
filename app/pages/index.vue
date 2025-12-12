<template>
  <div class="container mx-auto py-10">
    <div class="card mb-4">
      <div class="flex justify-between items-center mb-6">
        <div>
          <p class="text-sm text-gray-600 mb-1">Welcome to</p>
          <h1 class="text-2xl font-bold">VBKOROA Nuxt Playground!</h1>
        </div>
      </div>
      <div class="flex justify-end">
        <button class="px-4 py-2 bg-blue-600 text-white rounded hover:bg-blue-700" @click="count++">
          클릭한 횟수: {{ count }}
        </button>
      </div>
    </div>
    <div class="card">
      <div class="font-semibold text-xl mb-3">액션 로그</div>
      <div v-if="messages.length === 0" class="text-sm text-gray-400">
        아무런 로그가 없다!
      </div>
      <ul v-else class="space-y-1 text-sm">
        <li v-for="(msg, i) in messages" :key="i">{{ i + 1 }}. {{ msg }}</li>
      </ul>
      <div class="flex justify-end mt-4">
        <button class="px-3 py-1 bg-slate-600 text-white rounded" @click="messages.push(`버튼이 ${count}번 클릭되었습니다!`)">
          로그 추가
        </button>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const count = ref(0);
const messages = ref<string[]>([]);
</script>
