<script setup>
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Navigation } from 'vue3-carousel'
import { onMounted, ref, toRefs } from 'vue'
import { Link } from '@inertiajs/vue3';

let wWidth = ref(window.innerWidth)
let currentSlide = ref(0)

const props = defineProps({ posts: Object, allUsers: Object })
const { posts, allUsers } = toRefs(props)

onMounted(() => {
    window.addEventListener('resize', () => {
        wWidth.value = window.innerWidth
    })
})

</script>

<template>
    <Carousel
        v-model="currentSlide"
        class="max-w-[700px] mx-auto border-2 rounded-lg bg-white"
        :items-to-show="wWidth >= 768 ? 8 : 6"
        :items-to-scroll="4"
        :wrap-around="true"
        :transition="500"
        snapAlign="start"
        >
        <Slide v-for="slide in 10" :key="slide">
            <Link href="/" class="relative mx-auto text-center mt-4 px-2 cursor-pointer">
                <div class="absolute z-[-1] -top-[5px] left-[4px] rounded-full rotate-45 w-[64px] h-[64px] contrast-[1.3]  bg-gradient-to-t from-yellow-300 to-purple-500 via-red-500">
                    <div class="rounded-full ml-[3px] mt-[3px] w-[58px] h-[58px] bg-white" />
                </div>
                <img class="rounded-full object-contain w-[56px] h-[56px] -mt-[1px]" src="/img.jpg">
                <div class="text-xs mt-2 w-[60px] truncate text-ellipsis overflow-hidden">mukai_jakypbekov</div>
            </Link>
        </Slide>

        <template #addons>
            <Navigation />
        </template>
    </Carousel>
</template>

<style>
    .carousel__prev,
    .carousel__next,
    .carousel__prev:hover,
    .carousel__next:hover {
        color: rgb(49, 49, 49);
        background-color: rgb(255, 255, 255);
        border-radius: 100%;
        margin: 0 20px;
    }
</style>
