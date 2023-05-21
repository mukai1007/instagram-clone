<script setup>
import Heart from 'vue-material-design-icons/Heart.vue';
import HeartOutline from 'vue-material-design-icons/HeartOutline.vue';
import CommentOutline from 'vue-material-design-icons/CommentOutline.vue';
import SendOutline from 'vue-material-design-icons/SendOutline.vue';
import BookmarkOutline from 'vue-material-design-icons/BookmarkOutline.vue';

</script>

<template>
    <div class="flex z-20 items-center justify-between">
        <div class="flex items-center px-2">
            <button class="-mt-[14px]">
                <HeartOutline class="pl-3 cursor-pointer" :size="25" />
                <!-- <Heart v-else class="pl-3 cursor-pointer" fillColor="#FF0000" :size="30" /> -->
            </button>
            <CommentOutline class="pl-3 pt-[10px] cursor-pointer" :size="25" />
            <SendOutline class="pl-3 pt-[10px] cursor-pointer" :size="25" />
        </div>

        <BookmarkOutline class="px-3  pt-[10px] cursor-pointer" :size="25" />
    </div>
</template>
