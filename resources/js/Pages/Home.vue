<script setup>
import Post from '@/Components/Post.vue';
import Stories from '@/Components/Stories.vue';

import MainLayout from '@/Layouts/MainLayout.vue';
import { Head, Link } from '@inertiajs/vue3';

</script>

<template>
    <MainLayout>
        <div class="mx-auto lg:pl-0 md:pl-[80px] pl-0">
            <Stories/>
            <Post/>
            <Post/>
        </div>
    </MainLayout>
</template>
