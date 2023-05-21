<script setup>
import { ref, reactive } from 'vue';

import Close from 'vue-material-design-icons/Close.vue';
import ArrowLeft from 'vue-material-design-icons/ArrowLeft.vue';
import MapMarkerOutline from 'vue-material-design-icons/MapMarkerOutline.vue';
import ChevronDown from 'vue-material-design-icons/ChevronDown.vue';

const emit = defineEmits(['close'])

const form = reactive({
        text: null,
        file: null,
    })

const isValidFile = ref(null)
const fileDisplay = ref('')
const textarea = ref('')
const error = ref({
    text: null,
    file: null,
})

const uploadImage = (e) => {
    form.file = e.target.files[0]
    const extention = form.file.name.substring(form.file.name.lastIndexOf('.') + 1);

    if (extention == 'png' || extention == 'jpg' || extention == 'jpeg') {
        isValidFile.value = true
        console.log('true');
    } else {
        isValidFile.value = false
        return
    }

    fileDisplay.value = URL.createObjectURL(e.target.files[0])
    setTimeout(() => {
            document.getElementById('TextAreaSection').scrollIntoView({behavior: 'smooth'});
    }, 300);
}

const closeModal = () => {
    form.value = {
        text: '',
        file: ''
    }
    fileDisplay.value = ''
    emit('close')
}

</script>

<template>
  <div id="CreatePostModal" class="fixed z-50 top-0 left-0 w-full h-screen bg-[#000000] bg-opacity-60 p-3">

        <button class="absolute right-3 cursor-pointer" @click="closeModal()">
            <Close :size="27" fillColor="#FFFFFF"/>
        </button>

        <div class="max-w-4xl h-[calc(100%-100px)] mx-auto mt-10 bg-white rounded-xl">
            <div class="flex items-center justify-between w-full rounded-t-xl p-3 border-b border-b-gray-300">
                <ArrowLeft :size="30" fillColor="#000000" @click="closeModal()" class="cursor-pointer"/>
                <div class="text-[16px] font-extrabold">Создание публикации</div>
                <button @click="createPost()" class=" text-[14px] text-blue-500 hover:text-gray-600 font-extrabold">
                    Поделиться
                </button>
            </div>

            <div class="w-full md:flex h-[calc(100%-55px)] rounded-xl overflow-auto">
                <div id="UploadImage" class="flex items-center bg-gray-100 w-full h-full overflow-hidden">
                    <div v-if="!fileDisplay" class="flex flex-col items-center mx-auto">
                        <label
                            for="file"
                            class="hover:bg-blue-700 bg-blue-500 rounded-lg p-2.5 text-white font-extrabold cursor-pointer"
                        >
                            Выбрать на компьютере
                        </label>
                        <input
                            id="file"
                            class="hidden"
                            type="file"
                            @input="uploadImage($event)"
                        >
                        <div v-if="error && error.file" class="text-red-500 text-center p-2 font-extrabold">error</div>
                        <div v-if="!fileDisplay && isValidFile === false" class="text-red-500 text-center p-2 font-extrabold">
                            Файл не принят
                        </div>
                    </div>
                    <img v-if="fileDisplay && isValidFile === true" class=" min-w-[400px] p-4 mx-auto" :src="fileDisplay"/>
                </div>

                <div id="TextAreaSection" class="max-w-[350px] w-full relative">
                    <div class="flex items-center justify-between p-3">
                        <div class="flex items-center">
                            <img class="rounded-full w-[38px] h-[38px]" src="/user-placeholder.png">
                            <div class="ml-4 font-extrabold text-sm">mukai_jakypbekov</div>
                        </div>
                    </div>

                    <div v-if="error && error.text" class="text-red-500 p-2 font-extrabold">error</div>

                    <div class="flex w-full max-h-[200px] bg-white border-b">
                        <textarea
                            ref="textarea"
                            v-model="form.text"
                            placeholder="Добавьте подпись..."
                            rows="10"
                            class="
                              placeholder-gray-500
                                w-full
                                border-0
                                mt-2
                                mb-2
                                z-50
                                focus:ring-0
                                text-gray-600
                                text-[18px]
                            "
                        ></textarea>
                    </div>

                    <div class="flex items-center justify-between border-b p-3">
                        <div class="text-[16px] font-medium text-gray-500">Довавить место</div>
                        <MapMarkerOutline :size="25"/>
                    </div>

                    <div class="flex items-center justify-between border-b p-3">
                        <div class="text-[16px] font-medium text-gray-500">Специальные возможности</div>
                        <ChevronDown :size="25"/>
                    </div>

                    <div class="flex items-center justify-between border-b p-3">
                        <div class="text-[16px] font-medium text-gray-500">Расширенные настройки</div>
                        <ChevronDown :size="25"/>
                    </div>
                </div>
            </div>
        </div>
  </div>
</template>
