<template>
  <UContainer class="py-10">
    <UCard>
      <div class="flex justify-between items-center mb-6">
        <div>
          <p class="text-sm opacity-70 mb-1">Welcome to</p>
          <h1 class="text-2xl font-bold">VBKOROA Nuxt Playground!</h1>
        </div>
      </div>
      <UButton
        color="primary"
        @click="count++"
      >
        클릭한 횟수: {{ count }}
      </UButton>
    </UCard>
  </UContainer>
</template>

<script setup lang="ts">
  const count = ref(0)
</script>