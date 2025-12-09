<template>
    <UContainer>
        <!--- Header -->
        <UHeader to="/todos">
            <template #title>
                Todos
            </template>
            <p>8 기 공 식 미 녀 박 수 현</p>
        </UHeader>
        <!--- main -->
            <UCard class="my-4">
                <template #header>
                    <p>할 일 추가</p>
                </template>
                <UForm class="flex" @submit="addTodo">
                    <UInput v-model="todoTitle" color="neutral" placeholder="제목" class="flex-1"></UInput>
                    <UInput v-model="todoContents" color="neutral" placeholder="내용" class="flex-2 mx-2"></UInput>
                    <UButton class="px-4" type="submit">제출</UButton>
                </UForm>
            </UCard>
            <UCard>
                <template #header>
                    <p>할 일 목록</p>
                </template>
                <UTable :data="todos" :columns="columns"></UTable>
            </UCard>
        <!--- footer -->
        <UFooter>
            <p class="font-semibold">Copyright © ABKO</p>
        </UFooter>
    </UContainer>
</template>

<script setup lang="ts">
import type { TableColumn } from '@nuxt/ui';

    type Todo = {
        id: number;
        title: string;
        contents: string;
        createdAt: Date;
    }

    const todoTitle = ref<string>('')
    const todoContents = ref<string>('')
    const todos = ref<Todo[]>([])
    
    const columns: TableColumn<Todo>[] = [
        {accessorKey: 'id'},
        {
            accessorKey: 'createdAt',
            header: '작성일',
            cell: ({row}) => row.original.createdAt.toLocaleString('ko-KR', {
                dateStyle: 'short',
                timeStyle: 'short'
            })
        },
        {accessorKey:'title', header: '제목'},
        {accessorKey:'contents', header: '내용'}
    ]

    let id = 0;

    const addTodo = () => {
        todos.value.push({
            id: id++,
            title: todoTitle.value,
            contents: todoContents.value,
            createdAt: new Date()
        });

        todoTitle.value = ''
        todoContents.value = ''
    }
</script>