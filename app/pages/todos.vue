<template>
  <div class="container mx-auto p-4">
    <header class="mb-3">
      <div class="flex items-center justify-between">
        <h2 class="text-xl font-semibold">Todos</h2>
        <p class="text-black">8 기 공 식 미 녀 박 수 현</p>
      </div>
    </header>

    <section class="card my-4">
      <div class="mb-2 font-semibold">할 일 추가</div>
      <form class="flex" @submit.prevent="addTodo">
        <input v-model="todoTitle" placeholder="제목" class="flex-1 border rounded px-3 py-2" />
        <input v-model="todoContents" placeholder="내용" class="flex-2 mx-2 border rounded px-3 py-2" />
        <button class="px-4 bg-blue-600 text-white rounded" type="submit">제출</button>
      </form>
    </section>

    <section class="card">
      <div class="mb-2 font-semibold">할 일 목록</div>
      <table class="w-full table-auto">
        <thead class="border-b">
          <tr class="text-left">
            <th class="py-2">ID</th>
            <th class="py-2">작성일</th>
            <th class="py-2">제목</th>
            <th class="py-2">내용</th>
            <th class="py-2">삭제</th>
          </tr>
        </thead>
        <tbody>
          <tr v-if="todos.length === 0" class="text-center table-row w-full justify-center">
            <td colspan="5">할 일이 없습니다.</td>
          </tr>
          <tr v-for="todo in todos" :key="todo.id" class="border-b-gray-500 border-b">
            <td class="py-2 font-bold">{{ todo.id }}</td>
            <td class="py-2">{{ todo.createdAt.toLocaleString('ko-KR', { dateStyle: 'short', timeStyle: 'short' }) }}</td>
            <td class="py-2">{{ todo.title }}</td>
            <td class="py-2">{{ todo.contents }}</td>
            <td class="py-2"><button class="px-2 py-1 bg-red-600 text-white rounded" @click="removeTodo(todo.id)">삭제</button></td>
          </tr>
        </tbody>
      </table>
    </section>

    <footer class="mt-4 text-center text-sm text-gray-600">Copyright © ABKO</footer>
  </div>
</template>

<script setup lang="ts">

type Todo = {
  id: number;
  title: string;
  contents: string;
  createdAt: Date;
};

const todoTitle = ref<string>('');
const todoContents = ref<string>('');
const todos = ref<Todo[]>([]);

let id = 0;

const addTodo = () => {
  todos.value.push({
    id: id++,
    title: todoTitle.value,
    contents: todoContents.value,
    createdAt: new Date(),
  });

  todoTitle.value = '';
  todoContents.value = '';
};

const removeTodo = (id: number) => {
  todos.value = todos.value.filter((todo) => todo.id !== id);
};
</script>
