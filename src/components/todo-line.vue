<template>
    <v-hover>
        <template v-slot:default="{ isHovering, props }">
            <v-sheet border="borderColor b-sm" v-bind="props"
                class="cursor-pointer w-100 d-flex ga-3 align-center justify-space-between px-5 py-3 bg-surface"
                :class="{ 'rounded-top': roundedCorner }" @click="appStore.toggleActiveState(todo.id)">
                <div class="dot" :class="[todo.isCompleted ? 'dot-completed-todo' : 'bg-transparent']">
                    <v-icon v-if="todo.isCompleted" color="white" class="mb-3" icon="mdi-check" size="x-small" />
                </div>
                <div class="flex-grow-1 text-truncate"
                    :class="{ 'text-decoration-line-through': isHovering || todo.isCompleted, 'text-veryDarkGrayishBlue': todo.isCompleted }">
                    {{ todo.title }}
                </div>
                <v-btn v-if="isHovering" max-height="28px" icon="mdi-close" variant="plain" size="x-small"
                    @click.prevent="appStore.deleteTodo(todo.id)" />
            </v-sheet>
        </template>
    </v-hover>
</template>

<style scoped>
.rounded-top {
    border-top-left-radius: 10px;
    border-top-right-radius: 10px;
}

.dot-completed-todo {
    background: linear-gradient(to left top, hsl(192, 100%, 67%), hsl(280, 87%, 65%));
    border-color: rgb(var(--v-theme-surface));
}
</style>

<script setup lang="ts">
import type { Todo } from "@/models/todos";
import { useAppStore } from '@/stores/app';

const appStore = useAppStore();

const props = defineProps<{
    todo: Todo,
    roundedCorner: boolean
}>();


</script>