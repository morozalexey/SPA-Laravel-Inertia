
<script setup>
    import { Link } from '@inertiajs/vue3'
    import MainLayout from '@/Layouts/MainLayout.vue'
    defineProps({ post: Object })
</script>

<template>
    <MainLayout>
        <h1 class="text-lg mb-2">Post</h1>
        <Link :href="route('post.index')" class="text-sky-500 text-sm">Back</Link>
        <div v-if="post" class="mt-8">
            <div class="mt-8 pt-8">
                <div class="mb-2">id: {{ post.id }}</div>
                <div class="mb-2">title: {{ post.title }}</div>
                <div class="mb-2">content: {{ post.content }}</div>
                <div class="mb-2 text-sm text-right">{{ post.date }}</div>
            </div>
        </div>
    </MainLayout>
</template>
