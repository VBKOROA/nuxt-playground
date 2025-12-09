<template>
  <UContainer class="py-10">
    <UCard class="mb-4">
      <div class="flex justify-between items-center mb-6">
        <div>
          <p class="text-sm opacity-70 mb-1">Welcome to</p>
          <h1 class="text-2xl font-bold">VBKOROA Nuxt Playground!</h1>
        </div>
      </div>
      <div class="flex justify-end">
        <UButton color="primary" @click="count++">
          클릭한 횟수: {{ count }}
        </UButton>
      </div>
    </UCard>
    <UCard>
      <template #header>
        <span class="font-semibold text-xl">액션 로그</span>
      </template>
      <div v-if="messages.length === 0" class="text-sm text-gray-400">
        아무런 로그가 없다!
      </div>
      <ul v-else class="space-y-1 text-sm">
        <li v-for="(msg, i) in messages" :key="i">{{ i + 1 }}. {{ msg }}</li>
      </ul>
      <template #footer>
        <div class="flex justify-end">
          <UButton
            size="sm"
            color="secondary"
            @click="messages.push(`버튼이 ${count}번 클릭되었습니다!`)"
          >
            로그 추가
          </UButton>
        </div>
      </template>
    </UCard>
  </UContainer>
</template>

<script setup lang="ts">
const count = ref(0);
const messages = ref<string[]>([]);
</script>
