<template>
    <div id="app" class="relative w-screen h-screen flex">
        <router-view />

        <!-- Bottom Nav -->
        <!-- <div
            class="z-20 fixed bottom-0 w-screen h-16 bg-white border-t border-gray-200"
        >
            <button @click="toggleAlphabetVisibility">alphabet</button>
        </div> -->

        <!-- <transition name="fade">
            <div
                v-if="showAlphabet"
                class="fixed w-full h-full top-0 left-0 pt-20 bg-black bg-opacity-25"
            />
        </transition>

        <transition name="slide-up">
            <div
                v-if="showAlphabet"
                class="fixed w-full h-full top-0 left-0 py-16"
            >
                <div
                    class="w-full h-full flex flex-col bg-white border rounded-t-3xl shadow-xl"
                >
                    <div class="w-full grid grid-cols-4 overflow-auto">
                        <router-link
                            v-for="character in alphabet"
                            :key="character.id"
                            :to="{
                                name: 'Character',
                                params: { id: character.id }
                            }"
                            class="h-20 w-full inline-flex items-center justify-center text-4xl text-gray-800 bg-white rounded border border-white opacity-25"
                            :class="{ 'text-red-500': character.vowel }"
                            @click.native="toggleAlphabetVisibility"
                        >
                            {{ character.variants.isolated }}
                        </router-link>
                    </div>
                </div>
            </div>
        </transition> -->
    </div>
</template>

<script>
import Vue from 'vue';
import { alphabet } from '~/enums';

export default Vue.extend({
    name: 'App',
    data() {
        return {
            alphabet,
            showAlphabet: false,
        };
    },
    methods: {
        toggleAlphabetVisibility() {
            this.showAlphabet = !this.showAlphabet;
        },
    },
});
</script>

<style scoped>
.fade-enter-active, .fade-leave-active {
    transition: opacity 0.5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
}

.slide-up-enter-active, .slide-up-leave-active {
    transition: top 0.5s;
}
.slide-up-enter, .slide-up-leave-to /* .fade-leave-active below version 2.1.8 */ {
    top: 100%;
}
</style>
