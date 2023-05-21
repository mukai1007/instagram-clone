<script setup>
import HomeOutline from 'vue-material-design-icons/HomeOutline.vue';
import Magnify from 'vue-material-design-icons/Magnify.vue';
import Compass from 'vue-material-design-icons/Compass.vue';
import Video from 'vue-material-design-icons/MessageVideo.vue';
import SendOutline from 'vue-material-design-icons/SendOutline.vue';
import HeartOutline from 'vue-material-design-icons/HeartOutline.vue';
import Plus from 'vue-material-design-icons/Plus.vue';
import AccountOutline from 'vue-material-design-icons/AccountOutline.vue';
import Menu from 'vue-material-design-icons/Menu.vue';
import Logout from 'vue-material-design-icons/Logout.vue';

import { toRefs, ref } from 'vue';

const props = defineProps({iconString: String})
const { iconString } = toRefs(props)

let icon = null

if (iconString.value === 'Главная') icon = HomeOutline
if (iconString.value === 'Поисковый запрос') icon = Magnify
if (iconString.value === 'Интересное') icon = Compass
if (iconString.value === 'Reels') icon = Video
if (iconString.value === 'Сообщения') icon = SendOutline
if (iconString.value === 'Уведомления') icon = HeartOutline
if (iconString.value === 'Создать') icon = Plus
if (iconString.value === 'Профиль') icon = AccountOutline
if (iconString.value === 'Выйти') icon = Logout
</script>

<template>
    <div class="w-full xl:inline-block xl:hover:bg-gray-100 p-2 rounded-full transition duration-300 ease-in-out cursor-pointer">
        <div class="flex items-center">
            <img
                v-if="iconString === 'Профиль'"
                :class="{'mr-1': iconString === 'Профиль'}"
                class="rounded-full ml-[2px] w-[30px] cursor-pointer"
                src="/user-placeholder.png"
            >
            <component v-else :is="icon" :size="30"/>
            <span class="xl:block hidden text-black font-medium text-[16px] pl-2 mt-0.5">
                {{ iconString }}
            </span>
        </div>
    </div>
</template>
