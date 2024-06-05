
<script setup>
    import { Link, useForm } from '@inertiajs/vue3'
    import MainLayout from '@/Layouts/MainLayout.vue'

    defineProps({ posts: Object })

    const form = useForm({});

    function destroy(id) {
        if (confirm("Are you sure you want to Delete")) {
            form.delete(route('post.destroy', id));
        }
    }

</script>

<template>
    <MainLayout>
        <h1 class="text-lg mb-8">Posts</h1>
        <div class="mb-8">
            <Link :href="route('post.create')" class="hover:bg-white hover:text-sky-500 border border-sky-500 block p-2 w-32 bg-sky-500 rounded-full text-center text-white">Add Post</Link>
        </div>
        <div v-if="posts">
            <div class="mt-8 pt-8 border-t border-gray-300" v-for="post in posts" >
                <div class="mb-2">id: {{ post.id }}</div>
                <div class="mb-2">title: {{ post.title }}</div>
                <div class="mb-2">content: {{ post.content }}</div>
                <div class="mb-2 text-sm text-right">{{ post.date }}</div>
                <div class="mb-2 text-sm text-right">
                    <Link :href="route('post.show', post.id)" class="text-sky-500 text-sm">More</Link>
                </div>
                <div class="mb-2 text-sm text-right">
                    <Link :href="route('post.edit', post.id)" class="text-sky-500 text-sm">Edit</Link>
                </div>
                <div class="mb-2 text-sm text-right">
                    <a href="" @click.prevent="destroy(post.id)" class="text-red-500 text-sm">Delete</a>
                </div>
            </div>
        </div>
    </MainLayout>
</template>
