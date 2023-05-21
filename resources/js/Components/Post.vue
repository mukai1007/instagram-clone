<script setup>
import LikesSection from './LikesSection.vue';
import DotsHorizontal from 'vue-material-design-icons/DotsHorizontal.vue';


</script>

<template>
    <div id="Posts" class="max-w-[470px] max-h-[635px] mx-auto border-[1px] border-gray-300 rounded-lg">
                <div class="flex items-center justify-between p-3">
                    <div class="flex items-center justify-between">
                        <Link href="/" class="flex items-center">
                            <img class="rounded-full object-contain bg-white w-[38px] h-[38px]" src="/img.jpg">
                            <div class="ml-4 font-extrabold text-[15px cursor-pointer">mukai_jakypbekov</div>
                        </Link>
                    </div>
                    <DotsHorizontal class="cursor-pointer" :size="27"/>
                </div>

                <div class="bg-black w-full min-h-[400px] flex items-center">
                    <img class="mx-auto object-cover w-[468px] h-[400px]" src="/200.jpeg" />
                </div>

                <LikesSection/>

                <div class="text-black font-bold py-2 px-3 text-sm">200 отметок "Нравится"</div>
                <div> 
                    <span class="text-black font-bold text-sm pl-3 py-2">mukai_jakypbekov</span>
                    Toyota Land Cruser 200
                </div>
                <button
                    class="text-gray-500 text-sm px-3 py-2"
                >
                    Посмотреть комментарий (2)
                </button>
            </div>
            <div class="max-w-[470px] max-h-[635px] my-5 mx-auto border-b border-[1px] border-gray-300"></div>
</template>
