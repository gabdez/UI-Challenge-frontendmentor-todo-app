<template>
    <v-sheet v-if="appStore.todos.length > 0" min-height="48px"
        class="text-darkGrayishBlue rounded-bottom w-100 d-flex ga-3 justify-space-between align-center px-5 bg-surface">
        <div class="text-caption">
            {{ appStore.filteredTodos.length }} items left
        </div>
        <div v-if="$vuetify.display.mdAndUp">
            <v-btn-toggle v-model="appStore.toggleActive" mandatory>
                <v-btn value="all" variant="plain" size="x-small"
                    :class="{ 'text-primary': 'all' === appStore.toggleActive }">All</v-btn>
                <v-btn value="active" variant="plain" size="x-small"
                    :class="{ 'text-primary': 'active' === appStore.toggleActive }">Active</v-btn>
                <v-btn value="completed" variant="plain" size="x-small"
                    :class="{ 'text-primary': 'completed' === appStore.toggleActive }">Completed</v-btn>
            </v-btn-toggle>
        </div>
        <v-btn variant="text" size="x-small" @click="appStore.clearCompletedTodos">Clear Completed</v-btn>
    </v-sheet>
</template>

<style scoped>
.rounded-bottom {
    border-bottom-left-radius: 4px;
    border-bottom-right-radius: 4px;
}
</style>

<script setup lang="ts">
import { useAppStore } from '@/stores/app';

const appStore = useAppStore();

</script>