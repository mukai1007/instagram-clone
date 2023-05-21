<script setup>
import Stories from '@/Components/Stories.vue';
import MainLayout from '@/Layouts/MainLayout.vue';
import { Head, Link } from '@inertiajs/vue3';

</script>

<template>
    <Head title="Instagram" />
    <MainLayout>
        <div class="mx-auto lg:pl-0 md:pl-[80px] pl-0">
            <Stories/>
        </div>
    </MainLayout>
</template>
