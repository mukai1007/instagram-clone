<script setup>
import Magnify from 'vue-material-design-icons/Magnify.vue';
import HeartOutline from 'vue-material-design-icons/HeartOutline.vue';
import HomeOutline from 'vue-material-design-icons/HomeOutline.vue';
import Compass from 'vue-material-design-icons/Compass.vue';
import SendOutline from 'vue-material-design-icons/SendOutline.vue';
import Plus from 'vue-material-design-icons/PlusBoxOutline.vue';
import AccountOutline from 'vue-material-design-icons/AccountOutline.vue';
import ChevronLeft from 'vue-material-design-icons/ChevronLeft.vue';
import AccountPlusOutline from 'vue-material-design-icons/AccountPlusOutline.vue';
import Video from 'vue-material-design-icons/MessageVideo.vue';

import { ref } from 'vue';
import { Link } from '@inertiajs/vue3';

import MenuItem from '@/Components/MenuItem.vue';
import CreatePost from '@/Components/CreatePost.vue'

const showCreatePost = ref(false)

const randomUsers = [
    {name: 'Jakypbekov Mukai'},
    {name: 'Jakypbekov Mukai'},
    {name: 'Jakypbekov Mukai'},
    {name: 'Jakypbekov Mukai'},
    {name: 'Jakypbekov Mukai'},
]

</script>

<template>
      <div id="MainLayout" class="w-full h-screen">

        <!-- Top Navigation Home-->
        <div v-if="$page.url === '/'" id="TopNavHome" class="fixed z-30 md:hidden block w-full bg-white h-[61px] border-b border-b-gray-300">
            <div class="flex items-center justify-between h-full">
                <Link href="/">
                    <img class="w-[105px] ml-6 cursor-pointer" src="/insta-logo.png">
                </Link>

                <div class="flex items-center w-[50%]">
                    <div class="flex items-center w-full bg-gray-100 rounded-lg">
                        <Magnify class="ml-4" fillColor="#8E8E8E" :size="27"/>
                        <input
                            type="text"
                            placeholder="Поиск"
                            class="
                                bg-transparent
                                w-full
                                placeholder-[#8E8E8E]
                                border-0
                                ring-0
                                focus:ring-0
                            "
                        />
                    </div>

                    <HeartOutline class="pl-4 pr-3" fillColor="#000000" :size="27" />
                </div>
            </div>
        </div>

        <!-- Top Navigation User-->
        <div 
            v-if="$page.url !== '/'"
            id="TopNavUser"
            class="md:hidden block flex items-center justify-between z-30 w-full bg-white h-[61px] border-b border-b-gray-300"
        >
            <Link href="/" class="px-4">
                <ChevronLeft :size="30" class="cursor-pointer"/>
            </Link>
            <div class="text-center w-[100%] text-lg font-extrabold">Discovery Studio</div>
        </div>

        <!-- Left Sidebar -->
        <div id="Sidebar" class="fixed h-full bg-white xl:w-[240px] w-[80px] md:block hidden border-r border-r-gray-300">
            <Link href="/">
                <img class="xl:hidden block w-[25px] mt-10 ml-[25px] mb-10 cursor-pointer" src="/insta-logo-small.png">
                <img class="xl:block hidden w-[103px] mt-10 ml-6 mb-10 cursor-pointer" src="/insta-logo.png">
            </Link>

            <div class="px-3">
                <Link href="/">
                    <MenuItem iconString="Главная" class="mb-4"/>
                </Link>
                <MenuItem iconString="Поисковый запрос" class="mb-4"/>
                <MenuItem iconString="Интересное" class="mb-4"/>
                <MenuItem iconString="Reels" class="mb-4"/>
                <MenuItem iconString="Сообщения" class="mb-4"/>
                <MenuItem iconString="Уведомления" class="mb-4"/>
                <MenuItem @click="showCreatePost = true" iconString="Создать" class="mb-4"/>
                <MenuItem iconString="Профиль" class="mb-4"/>
            </div>

            <Link :href="route('logout')" as="button" method="post" class="absolute bottom-0 px-3 w-full">
                <MenuItem iconString="Выйти" class="mb-4"/>
            </Link>
        </div>

        <!-- Home Section -->
        <div class="flex lg:justify-between bg-gray-100 h-full w-[100%-240px] xl:pl-[240px] lg:pl-[100px] overflow-auto">
            <div
                class="mx-auto md:pt-6 pt-20"
                :class="$page.url === '/' ? 'lg:w-8/12 w-full' : 'max-w-[1200px]'"
            >   
                <!-- Main Section -->
                <main>
                    <slot />
                </main>
            </div>

            <!-- Recommendations Section -->
            <div v-if="$page.url === '/'" id="RecommendationsSection" class="lg:w-4/12 lg:block hidden text-black mt-10">
                <Link class="flex items-center justify-between max-w-[350px] px-3">
                    <div class="flex items-center">
                        <img class="bg-white rounded-full object-contain z-10 w-[56px] h-[56px]" src="/img.jpg">
                        <div class="pl-4">
                            <div class="text-black font-extrabold text-[14px]">mukai_jakypbekov</div>
                            <div class="text-gray-500 text-extrabold text-[14px]">Мукай Жакыпбеков</div>
                        </div>
                    </div>
                    <button class="text-blue-500 hover:text-gray-900 text-[12px] font-extrabold">
                        Переключиться
                    </button>
                </Link>
                <div class="max-w-[350px] flex items-center justify-between p-3">
                    <div class="text-gray-500 font-extrabold text-[14px]">Рекомендации для вас</div>
                    <button class="text-blue-500 hover:text-gray-900 text-[12px] font-extrabold">
                        Все
                    </button>
                </div>

                <!-- Random Users -->
                <div v-for="randUser in randomUsers" :key="randUser">
                    <Link class="flex items-center justify-between max-w-[350px] p-3">
                        <div class="flex items-center">
                            <img class="rounded-full z-10 w-[32px] h-[32px]" src="/user-placeholder.png">
                            <div class="pl-4">
                                <div class="text-black font-extrabold text-[14px]">{{ randUser.name }}</div>
                                <div class="text-gray-500 text-extrabold text-[12px]">Подписаны: ...</div>
                            </div>
                        </div>
                        <button class="text-blue-500 hover:text-gray-900 text-[12px] font-extrabold">
                            Подписаться
                        </button>
                    </Link>
                </div>

                <!-- Footer -->
                <div class="max-w-[300px] mt-5 text-[12px]">
                    <div class="text-gray-400">Информация . Помощь . Пресса . API . Вакансии . Конфиденциальность . Условия . Места . Язык . Русский . Meta Verified</div>
                    <div class="text-left text-gray-400 mt-4">© 2023 INSTAGRAM FROM META</div>
                </div>
            </div>
        </div>

        <!-- Bottom Navigation -->
        <div id="BottomNav" class="fixed z-30 bottom-0 w-full md:hidden flex items-center justify-around bg-white border-t py-2 border-t-gray-300">
            <Link href="/">
                <HomeOutline fillColor="#000000" :size="33" class="cursor-pointer" />
            </Link>
            <Magnify fillColor="#000000" :size="33" class="cursor-pointer" />
            <Plus @click="showCreatePost = true" fillColor="#000000" :size="33" class="cursor-pointer" />
            <Video fillColor="#000000" :size="33" class="cursor-pointer" />
            <Link>
                <img
                    class="w-[30px] rounded-full cursor-pointer"
                    src="/user-placeholder.png"
                >
            </Link>
        </div>
      </div>

      <CreatePost v-if="showCreatePost" @close="showCreatePost = false"/>
</template>