<script setup>
import MainLayout from '@/Layouts/MainLayout.vue';
import Content from '@/Components/Content.vue'
import { Head, Link } from '@inertiajs/vue3';

import Cog from 'vue-material-design-icons/Cog.vue';
import Grid from 'vue-material-design-icons/Grid.vue';
import PlayBoxOutline from 'vue-material-design-icons/PlayBoxOutline.vue';
import BookmarkOutline from 'vue-material-design-icons/BookmarkOutline.vue';
import AccountBoxOutline from 'vue-material-design-icons/AccountBoxOutline.vue';

</script>

<template>
    <MainLayout>
        <div class="pt-2 md:pt-3"></div>
        <div class="max-w-[880px] px-4 w-[100vw] mx-auto">
            <div class="flex items-center md:justify-between">
                <div class="w-[300px]">
                    <label for="fileUser">
                    <img
                        class="w-[150px] h-[150px] rounded-full mx-5 bg-white object-contain cursor-pointer"
                        src="/img.jpg"
                    >
                    </label>
                    <input
                        id="fileUser"
                        class="hidden"
                        type="file"
                        @input="getUploadedImage($event)"
                    > 
                </div>

                <div class="w-full">
                    <div class="flex items-center md:mb-8 mb-5">
                        <div class="md:mr-6 mr-3 rounded-lg text-[22px]">mukai_jakypbekov</div>
                        <button class="md:block hidden md:mr-6 p-1 px-4 rounded-lg text-sm font-bold bg-gray-200 hover:bg-gray-300">
                            Редактировать профиль
                        </button>
                        <Cog :size="28" class="cursor-pointer"/>
                    </div>
                    <button class="md:hidden mr-6 p-1 px-4 max-w-[260px] w-full rounded-lg text-[17px] font-extrabold bg-gray-100 hover:bg-gray-200">
                        Редактировать профиль
                    </button>
                    <div class="md:block hidden">
                        <div class="flex items-center text-[16px]">
                            <div class="mr-6">
                                <span class="font-extrabold">1</span>  публикаций
                            </div>
                            <div class="mr-6 cursor-pointer">
                                <span class="font-extrabold">123</span>  подписчиков
                            </div>
                            <div class="mr-6 cursor-pointer">
                                <span class="font-extrabold">456</span>  подписок
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>

        <!-- Mobile  -->
        <div class="md:hidden">
            <div class="w-full flex items-center justify-around border-t border-t-gray-300 mt-8">
                <div class="text-center p-3">
                    <div class="font-extrabold">1</div>
                    <div class="text-gray-400 font-semibold -mt-1.5">публикаций</div>
                </div>
                <div class="text-center p-3 cursor-pointer">
                    <div class="font-extrabold">43</div>
                    <div class="text-gray-400 font-semibold -mt-1.5">подписчиков</div>
                </div>
                <div class="text-center p-3 cursor-pointer">
                    <div class="font-extrabold">55</div>
                    <div class="text-gray-400 font-semibold -mt-1.5">подписок</div>
                </div>
            </div>

            <div class="w-full flex items-center justify-between border-t border-t-gray-300">
                <div class="p-3 w-1/4 flex justify-center border-t border-t-gray-900">
                    <Grid :size="28" fillColor="#0095F6" class="cursor-pointer"/>
                </div>
                <div class="p-3 w-1/4 flex justify-center">
                    <PlayBoxOutline :size="28" fillColor="#8E8E8E" class="cursor-pointer"/>
                </div>
                <div class="p-3 w-1/4 flex justify-center">
                    <BookmarkOutline :size="28" fillColor="#8E8E8E" class="cursor-pointer"/>
                </div>
                <div class="p-3 w-1/4 flex justify-center">
                    <AccountBoxOutline :size="28" fillColor="#8E8E8E" class="cursor-pointer"/>
                </div>
            </div>
        </div>

        <!-- Content Section -->
        <div id="ContentSection" class="md:pr-1.5 lg:pl-0 md:pl-[90px]">
            <div class="md:block mt-10 hidden max-w-[880px] border-t border-t-gray-300 mx-auto">
                <div class="flex items-center justify-between max-w-[600px] mx-auto font-bold text-gray-400 text-[12px]">
                    <div class="p-[17px] w-1/4 flex justify-center items-center border-t border-t-gray-900 cursor-pointer">
                        <Grid :size="20" fillColor="#000000"/>
                        <div class="ml-2 -mb-[1px] text-gray-900">ПУБЛИКАЦИИ</div>
                    </div>
                    <div class="p-[17px] w-1/4 flex justify-center items-center cursor-pointer">
                        <PlayBoxOutline :size="20" fillColor="#8E8E8E"/>
                        <div class="ml-2 -mb-[1px]">REELS</div>
                    </div>
                    <div class="p-[17px] w-1/4 flex justify-center items-center cursor-pointer">
                        <BookmarkOutline :size="20" fillColor="#8E8E8E"/>
                        <span class="ml-2 -mb-[1px]">СОХРАНЕННЫЕ</span>
                    </div>
                    <div class="p-[17px] w-1/4 flex justify-center items-center cursor-pointer">
                        <AccountBoxOutline :size="20" fillColor="#8E8E8E"/>
                        <span class="ml-2 -mb-[1px]">ОТМЕТКИ</span>
                    </div>
                </div>
            </div>

            <div class="grid md:gap-4 gap-1 grid-cols-3 relative">
                <Content/>
                <Content/>
                <Content/>
                <Content/>
            </div>

            <div class="pb-20"></div>
        </div>
    </MainLayout>
</template>
