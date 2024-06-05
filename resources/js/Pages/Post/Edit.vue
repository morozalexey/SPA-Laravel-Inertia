<script setup>
import { reactive } from 'vue'
import { Link, router, useForm  } from '@inertiajs/vue3'
import MainLayout from '@/Layouts/MainLayout.vue'

const props = defineProps({
    post: {
        type: Object,
        default: () => ({}),
    },
    errors: {
        type: Object,
        default: () => ({}),
    },
});

const form = useForm({
    id: props.post.id,
    title: props.post.title,
    content: props.post.content,
});


const submit = () => {
    form.post(route("post.update", props.post.id));
};


</script>

<template>
    <MainLayout>
        <h1 class="text-lg mb-8">Edit</h1>
        <Link :href="route('post.index')" class="text-sky-500 text-sm">Back</Link>
        <form @submit.prevent="submit" >
            <div class="mb-4 mt-3">
                <input v-model="form.title" type="text" placeholder="title" class="w-full rounded-full border-gray-300">
                <div v-if="errors.title" class="text-red-600 text-sm">{{ errors.title }}</div>
            </div>
            <div class="mb-4">
                <textarea v-model="form.content" name="" id="" placeholder="content" class="w-full rounded-full border-gray-300"></textarea>
                <div v-if="errors.content" class="text-red-600 text-sm">{{ errors.content }}</div>
            </div>
            <div>
                <button type="submit" class="ml-auto hover:bg-white hover:text-sky-500 border border-sky-500 block p-2 w-32 bg-sky-500 rounded-full text-center text-white">Update</button>
            </div>
        </form>


    </MainLayout>
</template>
